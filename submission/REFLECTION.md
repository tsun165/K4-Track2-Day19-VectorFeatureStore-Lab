# Reflection — Lab 19

**Tên:** _Đỗ Thái Sơn_
**Cohort:** _A20-K4_
**Path đã chạy:** _lite_

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Kết quả theo loại query:

- exact (BM25 thắng/ngang Hybrid): Do query chứa từ khóa kỹ thuật nguyên văn (verbatim), BM25 khớp chính xác tuyệt đối mà không cần embedding.
- paraphrase (Semantic/Vector ưu thế): Người dùng dùng từ đồng nghĩa/diễn giải lại; BM25 bị lỗi vocabulary mismatch (không khớp từ khóa), chỉ vector bắt được ngữ nghĩa.
- mixed (Hybrid thắng vượt trội): Tận dụng RRF để kết hợp cả điểm khớp từ khóa lẫn ngữ nghĩa mở rộng. Đây là dạng query phổ biến nhất của người dùng thực tế nên Hybrid đạt Precision@10 trung bình cao nhất.

Khi nào KHÔNG dùng Hybrid:

- Chọn Pure BM25: Khi cần độ trễ cực thấp (< 5–10ms), tài nguyên hạn chế (tiết kiệm RAM/chi phí GPU chạy embedding), hoặc dữ liệu đặc thù mã tra cứu (mã lỗi, số hiệu, mã SKU, tên hàm/biến).
- Chọn Pure Vector: Khi tìm kiếm đa phương thức (ảnh/âm thanh/text), đa ngôn ngữ (cross-lingual), hoặc văn bản mô tả trừu tượng, giàu ngữ nghĩa mà từ khóa không lặp lại.

---

## Điều ngạc nhiên nhất khi làm lab này

hiểu rõ được quy trình của 1 con rag: từ embedding, lưu trữ DB đên các bước search, cơ chế rerank, so sánh độ hiệu quả của chúng để chọn ra phương án tối ưu

---

## Bonus challenge

- [x] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
