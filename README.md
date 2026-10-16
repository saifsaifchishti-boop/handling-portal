# LMS Handler — Virtual University Student Management

Static site (sirf `index.html`). Koi build nahi chahiye.

## Deploy
1. Is folder ko GitHub repo (private rakhein) mein upload karein.
2. Vercel -> Add New Project -> repo select -> Deploy.
3. Login: `admin` / `admin123` -> Settings mein foran badal lein.

## Data safety
- Data browser (localStorage) mein save hota hai. Settings -> Export backup regularly karein.
- Delete kiye students Trash mein jaate hain (restore ho sakte hain).
- Optional: Supabase cloud sync (data kabhi zaya na ho, sab devices par same).

### Supabase setup (1 minute)
SQL Editor mein chalayein:

```sql
create table lms_data (id text primary key, data jsonb);
alter table lms_data enable row level security;
create policy "all" on lms_data for all using (true) with check (true);
```
Phir Project Settings -> API se URL aur anon key Settings -> Cloud sync mein daalein, "Auto-sync" on karein.
Note: anon key jis ke paas ho wo data padh sakta hai, isliye key kisi ko na dein aur repo private rakhein.

## LMS auto-fill
Settings mein "Fill LMS" bookmarklet bookmark bar mein drag karein. Student ke "LMS" button se LMS kholein, phir bookmark par click karein.

## Cards
- Student -> Fees tab -> subject-wise fee add karein, total auto banta hai -> "Fee Card" (download / WhatsApp / print).
- Student -> Quiz/GDB/Work tab -> kaam Done tick karein -> "Card" -> PNG download ya share.
- Card ka naam, subtitle, support number aur payment accounts: Settings -> Card & payment details.
