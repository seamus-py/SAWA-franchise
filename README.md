# SAWA Franchise Application Page — README
### File: `sawa-franchise.html`

---

## What It Does

This is a standalone webpage that replaces the Google Form for franchise applications. When a potential franchisee fills it in and hits **Submit Application**, their details are sent directly to `info@sawa.green` via a service called Formspree.

The form collects:
- Full name, phone number, email address
- Who they are applying on behalf of (individual farmer, cooperative, NGO, other)
- Institution / organisation name
- Full address
- Any additional information

After submitting, the applicant sees a **thank-you screen** confirming their application has been received. The Sawa team receives an email with all their details and can reply directly to the applicant.

---

## One-Time Setup (Required to Activate Email Sending)

The form uses a free service called **Formspree** to send submissions to your inbox. You only need to do this once.

### Step 1 — Create a Formspree Account
Go to **[formspree.io](https://formspree.io)** and sign up for a free account using `info@sawa.green`.

The free plan allows **50 submissions per month**, which is plenty for franchise enquiries. If you ever need more, paid plans are available.

### Step 2 — Create a New Form
Once logged in:
1. Click **+ New Form**
2. Give it a name, e.g. `Sawa Franchise Applications`
3. Set the destination email to `info@sawa.green`
4. Click **Create Form**

### Step 3 — Copy Your Endpoint
Formspree will give you a unique URL that looks like:
```
https://formspree.io/f/mykbgelk
```
Copy this URL.

### Step 4 — Paste It Into the File
Open `sawa-franchise.html` in any text editor. Near the bottom of the file, find this line:

```js
const FORMSPREE_ENDPOINT = 'https://formspree.io/f/mykbgelk';
```

Replace `mykbgelk` with your own form ID from Step 3. Save the file.

### Step 5 — Verify Your Email
Formspree will send a verification email to `info@sawa.green`. Click the link in that email to confirm. **Submissions will not be delivered until you do this.**

---

## What the Email Looks Like

When someone submits the form, you will receive an email at `info@sawa.green` that looks like this:

```
Subject: New SAWA Franchise Application

Full Name:        Budi Santoso
Phone Number:     +62 877 1234 5678
Email:            budi@example.com
Applicant Type:   Individual Farmer
Institution:      Koperasi Tani Maju
Full Address:     Jl. Raya No. 12, Majalengka, West Java 45411
Additional Info:  I have 2 hectares of land and 5 years experience...
```

You can reply directly to the email and it will go straight to the applicant's inbox.

---

## How to Use It on Your Website

Upload `sawa-franchise.html` to your website hosting provider and link to it from your **SAWA Franchise** page, replacing the current Google Form link.

Alternatively, the file can be opened directly in a browser as a local file for testing purposes — but the form submission will only actually send emails when the file is hosted online and the Formspree endpoint is set up.

---

## How to Change the Form Fields

Open `sawa-franchise.html` in a text editor. The form fields are in the section labelled `<form id="appForm">`.

### Changing Placeholder Text
Each input field has a `placeholder` attribute — this is the grey hint text shown before the user types. For example:

```html
<input type="text" name="Full Name" id="fullName" placeholder="e.g. Budi Santoso">
```

Change `"e.g. Budi Santoso"` to whatever hint text you prefer.

### Changing Field Labels
Each label is in a `<label>` tag just above its input. For example:

```html
<label>Full Name <span class="req">*</span></label>
```

Change `Full Name` to whatever you want the label to say. The `<span class="req">*</span>` is the green asterisk that marks required fields — keep this if the field is required, remove it if not.

### Adding a New Text Field
Copy and paste this block inside the form, adjusting the name and placeholder:

```html
<div class="field">
  <label>Your New Field Label</label>
  <input type="text" name="Your New Field Label" id="newField" placeholder="Hint text here">
</div>
```

### Making a Field Not Required
Fields are validated by the `validate()` function in the `<script>` section at the bottom. To make a field optional, find its ID in the validation list and remove that line.

---

## How to Change the "Why SAWA" Section

The four benefit cards at the top of the page (Real Climate Impact, Proven Model, Full Support, Community Value) are in the `<div class="why-strip">` section. Each card looks like this:

```html
<div class="why-card">
  <div class="wicon">🌍</div>
  <h3>Real Climate Impact</h3>
  <p>Every tonne of biochar produced permanently locks away carbon dioxide...</p>
</div>
```

Change the emoji, heading, and paragraph text to update each card. To add a fifth card, copy the entire block and paste it inside `<div class="why-grid">`.

---

## How to Change Contact Details

The contact bar at the bottom of the form shows the Sawa phone number, email, Instagram, and website. Search the file for `+62 877-8964-7000` and update all instances. Do the same for `info@sawa.green` and `@sawa.ecosolutions`.

---

## How to Change the Success Message

After a successful submission, the applicant sees a thank-you screen. Find the section `<div class="success-screen" id="successScreen">` and edit the heading and paragraph text inside it.

---

## Troubleshooting

| Problem | Solution |
|---|---|
| Form submits but no email received | Check you verified your email in Formspree. Check your spam folder. |
| "Something went wrong" error | Check your Formspree endpoint URL is correct and your account is active. |
| Form shows an alert and won't submit | The Formspree endpoint URL is still set to a placeholder — follow the setup steps above. |
| More than 50 submissions per month needed | Upgrade to a paid Formspree plan at formspree.io/pricing |

---

## Summary Checklist

- [ ] Created Formspree account at formspree.io
- [ ] Created a new form with destination `info@sawa.green`
- [ ] Copied the endpoint URL into `sawa-franchise.html`
- [ ] Verified email address via Formspree confirmation email
- [ ] Uploaded file to website and linked from the franchise page
- [ ] Tested with a real submission to confirm email delivery
