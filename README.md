# Smart-Nutrition-Calculator
🧮 Smart Nutrition Calculator

A comprehensive, single‑file HTML/CSS/JS tool that calculates daily nutrition targets based on user inputs (weight, age, height, gender, goal, activity level, pregnancy status) and generates a downloadable diet plan.

---

✨ Features

Core Functionality

· Smart Nutrition Calculation – Calculates daily calories, protein, fat, fiber, carbohydrates, and water using standard formulas
· Goal‑Based Targeting – Supports four primary goals:
  · Maintain weight – Keep current weight or set a custom target
  · Match normal BMI – Automatically calculates target weight for BMI 22
  · Gain weight – Set target weight and time period (weeks)
  · Lose weight – Set target weight and time period (weeks)
· Pregnancy Adjustment – For female users, adds extra calories (+0/+340/+450 kcal/day) and protein (+0/+25/+25 g/day) based on trimester
· Activity Level – 5 levels from Sedentary to Very Active (1.2 – 1.9 multiplier)
· BMI Display – Live BMI calculation with visual color‑coded scale (underweight → normal → overweight → obese)

Interactive UI

· Live Updates – BMI updates in real‑time as you type weight or height
· Macro Pie Chart – Visual breakdown of daily protein, fat, and carbs with percentage labels
· Metric/Imperial Toggle – Switch between kg/cm and lbs/in
· LocalStorage – Automatically saves form state; restores on refresh (24‑hour expiry)
· Responsive Design – Optimized for desktop, tablet, and mobile screens

Diet Plan Generation

· Modal Form – Collects user's name, email, and additional health notes
· Downloadable TXT – Generates a complete diet plan file containing:
  · Personal information (name, email, gender, age, weight, height, BMI, activity, goal, target weight)
  · Daily nutrition targets (calories, protein, fat, fiber, carbs, water)
  · Calorie adjustment details (surplus/deficit)
  · Pregnancy adjustments (if applicable)
  · AI and formula disclaimer
· Email Instruction – After download, prompts user to send the file to the dietitian at abc@gmail.com

Accessibility & UX

· Proper for attributes on all form labels for screen readers
· Tooltips on Goal and Activity fields explaining options
· Number input spinners hidden on mobile for cleaner interaction
· Keyboard navigation support (Tab, Enter to calculate)
· Success messages with manual close and auto‑dismiss

---

🧪 Calculation Logic

Formulas Used

Nutrient Formula
BMR (Mifflin‑St Jeor) Male: 10 × weight + 6.25 × height − 5 × age + 5 Female: 10 × weight + 6.25 × height − 5 × age − 161
Maintenance Calories BMR × Activity
Pregnancy Adjustment Trimester 1: +0 kcal Trimester 2: +340 kcal, +25g protein Trimester 3: +450 kcal, +25g protein
Calorie Target Maintenance + Surplus/Deficit (capped at ±1000 kcal/day)
Protein Weight × 2.0 + Pregnancy adjustment (minimum 30g)
Fat Calories ÷ 30 (minimum 15g)
Fiber Calories × 0.014 (minimum 10g)
Carbs (Calories − Protein×4 − Fat×9) ÷ 4 (minimum 20g)
Water Weight × 0.035 + Activity bonus (minimum 1.5L)

Goal Adjustments

Goal Calculation
Maintain Calories = Maintenance
Match BMI Target = BMI 22 × (height in m)²; gradual adjustment over ~12 weeks
Gain Surplus = (Target − Weight) × 7700 ÷ (Weeks × 7)
Lose Deficit = (Weight − Target) × 7700 ÷ (Weeks × 7)

---

📁 File Structure

```
index.html   # Complete single‑file application (HTML + CSS + JS)
```

All code is contained in one HTML file. No external dependencies or build tools required.

---

🚀 Getting Started

Option 1: Direct Use

1. Download index.html
2. Open the file in any modern web browser
3. Enter your personal details and click Calculate Nutrients
4. Click Request Diet Plan to open the modal, fill in your name/email, and download your plan

Option 2: Host Online

Upload the file to any static hosting service (GitHub Pages, Netlify, Vercel, etc.) and access it via URL.

Option 3: Embed

```html
<!-- Copy the entire content of index.html into your project -->
```

---

🎯 How to Use

Step 1: Enter Personal Details

· Weight – in kg or lbs (toggle units)
· Age – in years
· Gender – Male / Female / Other
· Height – in cm or inches
· Pregnancy – (Female only) Select if pregnant and trimester

Step 2: Set Goal & Activity

· Goal – Maintain / Match Normal BMI / Gain / Lose
· Activity Level – Sedentary → Very Active

Step 3: Configure Target (if applicable)

· Maintain – Optional custom target weight
· BMI – Auto‑calculated (no manual entry needed)
· Gain / Lose – Enter target weight and time period (weeks)

Step 4: Calculate Nutrients

Click Calculate Nutrients – the display updates with your daily targets and macro chart.

Step 5: Request Diet Plan

1. Click Request Diet Plan (only active after calculation)
2. Fill in your Full Name, Email, and any Additional Notes
3. Agree to the Terms & Conditions
4. Click Request Diet Plan to download the .txt file
5. Send the downloaded file to abc@gmail.com as instructed

---

🔧 Technical Details

Technologies

· HTML5 – Semantic markup, accessible forms
· CSS3 – Custom properties, flexbox, responsive design, dark theme
· Vanilla JavaScript – No external libraries; ES6+ syntax

Browser Support

Browser Version
Chrome 90+
Firefox 88+
Safari 14+
Edge 90+
Mobile Chrome/Safari Latest

Dependencies

None. The tool is completely self‑contained and works offline after the page loads.

Performance

· Debounced BMI updates (250ms delay) for smooth typing experience
· Efficient canvas rendering for macro chart
· Lightweight DOM manipulation

---

📝 Customization

Change Dietitian Email

To update the email address shown after download, locate this line in the JavaScript:

```javascript
successDiv.innerHTML = `
    ✅ Diet plan downloaded successfully!<br>
    <strong>Please send this file to our dietitian at abc@gmail.com to get your personalized plan.</strong>
    ...
`;
```

Replace abc@gmail.com with your own email address.

Modify Formulas

Edit the calculateNutrition() function in the JavaScript section (around line 650):

· Adjust the base BMR formula
· Change macro percentages (protein, fat, carbs)
· Modify water calculation (currently weight × 0.035 + activity bonus)

Styling

All CSS is contained within the <style> section. Customize colors, spacing, fonts, and responsiveness by editing the CSS variables at the top of the style block.

---

🤝 Contributing

While this is a single‑file tool, contributions are welcome:

1. Fork the repository
2. Make your changes
3. Test thoroughly (desktop + mobile)
4. Submit a pull request

---

📄 License

MIT License – free for personal and commercial use.

---

⚠️ Disclaimer

This tool is for informational purposes only and does not replace professional medical advice. Always consult a healthcare provider before starting any diet or nutrition plan.

---

📞 Support

For issues or questions:

· Open an issue on GitHub
· Email support: support@example.com

---

Made with ❤️ for better nutrition planning.
