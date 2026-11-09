# Example prompts

Results below were captured on 2026-11-08 and 2026-11-09 and trimmed. Numbers change as new filings arrive.

## Who controls a company, directly and indirectly

> Who indirectly owns Samsung Electronics, and through which companies?

`get_holders` returns direct holders plus `indirect_holders`, traced through other listed companies:

| Holder | Indirect stake | Path |
|---|---|---|
| 이재용 (Lee Jae-yong) | 2.38% | 삼성물산 22.01% → 삼성전자 5.11% |
| 삼성물산 (Samsung C&T) | 1.66% | 삼성생명 19.34% → 삼성전자 8.57% |
| 이부진 (Lee Boo-jin) | 0.93% | 삼성물산 6.45% → 삼성전자 5.11% |

## What a holder paid

> What did Pan Ocean's largest shareholder pay per share?

`get_avg_cost` (ticker `028670`):

| Holder | Average cost | Basis |
|---|---|---|
| 하림지주 (Harim Holdings) | ₩5,127 | partial: only part of the stake has prices in the filings |
| 국민연금공단 (NPS) | none | short-form filing, prices omitted by law |

## What the National Pension Service did this week

> Every stock NPS cut in the last 7 days

`get_recent_changes` with `holder: "국민연금"` returned 9 filings, 4 of them decreases. Each row carries the filing date, the trade date when given, and a DART link.

## Find a foreign institution by its Korean name

> Korean stocks where BlackRock holds over 5%

`search_holder("블랙록")` finds the separate BlackRock entities that file in Korea (BlackRock Fund Advisors, BlackRock Institutional Trust Company, N.A., and others), each with its own `entity_id`. `get_portfolio` then lists what each one holds.

## What actually happened in one filing

> A fund took 21% of Bluemtec. Was it a market purchase, and at what price?

`get_filing` with the filing's DART link or its 14-digit receipt number (`20261106000426`):

| Trade date | Method | Shares | Price |
|---|---|---|---|
| 2026-10-30 | 장외매수 (off-market purchase) | +7,131,777 → 7,131,777 | ₩3,235 |

The filing date is 2026-11-06, a week after the trade. `reports` shows the stake (21.07%, new) and the reason given in the filing; `members` lists each filer and special-relationship party.

## More to try

- Show the ownership history of Kakao since 2025
- Which stocks did 김범수 file on in the last year?
- New 5% holders this week, excluding new listings and debt-for-equity swaps
- Compare NPS's stake in SK hynix and Samsung Electronics
