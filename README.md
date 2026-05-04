# החופש לשחק — דף נחיתה לקורס של נטע

דף נחיתה ב־HTML יחיד עם 3 ערוצי הרשמה: וואטסאפ ישיר · טופס מובנה · תיאום שיחה.

## מה כבר עובד מהקופסה

✅ **כפתור וואטסאפ ענק** — שולח אליה ב־`+61 415 456 750` עם הודעה מוכנה
✅ **כפתור צף** בפינה שצמוד למסך אחרי שגוללים
✅ **טופס מובנה** (שם · טלפון · "מה מביא/ה אותך?") — שולח אליה את הנתונים בוואטסאפ מעוצב יפה. **בלי שירות חיצוני.**

## מה דורש סטאפ קצר

### 📅 כפתור תיאום שיחת היכרות (Calendly / TidyCal)

הכפתור מוסתר עד שמכניסים URL. שלבים:

1. הירשמי לאחת:
   - **Calendly** (חינם בסיסי) — https://calendly.com
   - **TidyCal** (תשלום חד־פעמי $30) — https://tidycal.com
2. צרי "Event Type" של 30 דק' — "שיחת היכרות לקורס"
3. העתיקי את ה־URL הציבורי (משהו כמו `https://calendly.com/netta/intro-call`)
4. בקובץ `index.html`, חפשי את `CONFIG` ומלאי:

```javascript
const CONFIG = {
    whatsappNumber: '61415456750',
    courseName: 'החופש לשחק',
    calendlyUrl: 'https://calendly.com/netta/intro-call'  // ⬅️ כאן
};
```

הכפתור יופיע אוטומטית מתחת לטופס.

### 📊 אנליטיקס (לדעת כמה לחצו / מאיפה הגיעו)

בראש `index.html` יש בלוק `<!-- ANALYTICS -->` עם 3 אופציות. בחרי אחת והסירי את ה־comment:

**אופציה 1 — Cloudflare Web Analytics** (הכי פשוטה, חינמית, פרטית):
1. https://www.cloudflare.com/web-analytics/ → "Add a site"
2. הכניסי את ה־URL של האתר
3. העתיקי את הטוקן ל־`<script ... data-cf-beacon='{"token": "..."}'>`

**אופציה 2 — Plausible** ($9/חודש, ממש נקי, פרטי):
1. https://plausible.io → צרי אתר
2. החליפי `YOUR_DOMAIN.com` בדומיין שלך

**אופציה 3 — Google Analytics 4** (חינמי, נפוץ):
1. https://analytics.google.com → צרי property
2. החליפי `G-XXXXX` ב־Measurement ID שלך

### אירועים שיירשמו אוטומטית

| אירוע | מתי |
|---|---|
| `cta_whatsapp` | לחיצה על הכפתור הענק בסקשן ההרשמה |
| `float_whatsapp` | לחיצה על הכפתור הצף |
| `form_submit` | שליחת טופס |
| `calendly_click` | לחיצה על תיאום שיחה |

ב־Plausible: יופיעו ב־"Goal Conversions". ב־GA4: ב־"Events" tab.

## עדכון פרטים

הכל מרוכז בבלוק `CONFIG` בתחתית `index.html`:

```javascript
const CONFIG = {
    whatsappNumber: '61415456750',  // ללא + או רווחים
    courseName: 'החופש לשחק',
    calendlyUrl: ''                  // ריק = הכפתור מוסתר
};
```

## תוכן

כל הטקסטים ישירות ב־HTML. שמות מודולים, פרטים, ציטוטים — חפשי ועדכני.

## הרצה מקומית

```bash
python3 -m http.server 8000
# פתח: http://localhost:8000
```

## פריסה

האתר חי דרך GitHub Pages על הבראנץ' `claude/setup-course-structure-DeULM`:
**https://oren001.github.io/cx-netta-59th-birthday-invitation-mo3te679/**

כל commit לבראנץ' הזה מתעדכן אוטומטית תוך 1–3 דקות.

## ארכיון

`v1.html` — `v6.html` שומרים את 6 הגרסאות העיצוביות שהוצעו בתחילת הדרך, למקרה שתרצי לחזור או לשלב.
