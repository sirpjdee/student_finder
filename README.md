<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Student Section Finder</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 2em;
      background: #f9f9f9;
      max-width: 600px;
      margin: auto;
    }
    h1 {
      text-align: center;
      color: #333;
    }
    input {
      width: 100%;
      padding: 12px;
      font-size: 1em;
      margin-top: 1em;
      box-sizing: border-box;
    }
    .result {
      margin-top: 1.5em;
      font-size: 1.2em;
      font-weight: bold;
      color: #2c3e50;
    }
  </style>
</head>
<body>
  <h1>Find Your Section</h1>
  <input type="text" id="nameInput" placeholder="Enter your name (e.g., Kevin James Almonte)" />
  <div class="result" id="result"></div>

  <script>
    const students = [
      { name: "Fheb Vincent Agbay", section: "Grade 11 - Aristotle" },
      { name: "Kevin James Almonte", section: "Grade 11 - Aristotle" },
      { name: "Luiz Vergel Aparece", section: "Grade 11 - Aristotle" },
      { name: "Kurt Atillo", section: "Grade 11 - Aristotle" },
      { name: "Kent Nathaniele Baang", section: "Grade 11 - Aristotle" },
      { name: "Dennielle Jake Bacon", section: "Grade 11 - Aristotle" },
      { name: "Crismark Benarao", section: "Grade 11 - Aristotle" },
      { name: "Johnzyle Brizo", section: "Grade 11 - Aristotle" },
      { name: "Albert Jr. Campugan", section: "Grade 11 - Aristotle" },
      { name: "Ginoly Cuizon", section: "Grade 11 - Aristotle" },
      { name: "Cris Tof Dayanan", section: "Grade 11 - Aristotle" },
      { name: "Rian Fabe", section: "Grade 11 - Aristotle" },
      { name: "John Mark Fernandez", section: "Grade 11 - Aristotle" },
      { name: "Christian Gako", section: "Grade 11 - Aristotle" },
      { name: "Dave Irona", section: "Grade 11 - Aristotle" },
      { name: "BB Jenboy Lausa", section: "Grade 11 - Aristotle" },
      { name: "Christian Lauron", section: "Grade 11 - Aristotle" },
      { name: "Richard Dems Lu-ang", section: "Grade 11 - Aristotle" },
      { name: "Jian James Nadela", section: "Grade 11 - Aristotle" },
      { name: "Jackris Pantilgan", section: "Grade 11 - Aristotle" },
      { name: "James Carl Racoma", section: "Grade 11 - Aristotle" },
      { name: "Criss Michol Remo", section: "Grade 11 - Aristotle" },
      { name: "June Vincent Satinitigan", section: "Grade 11 - Aristotle" },
      { name: "John Carlo Satinitigan", section: "Grade 11 - Aristotle" },
      { name: "Brian Lauron", section: "Grade 11 - Aristotle" },
      { name: "Negro Patrick Tangaro", section: "Grade 11 - Aristotle" },
      { name: "James Rich Traya", section: "Grade 11 - Aristotle" },
      { name: "Kienneth Tumulak", section: "Grade 11 - Aristotle" },
      { name: "Jushua Ray Yurango", section: "Grade 11 - Aristotle" },
      { name: "Mary Cris Amistad", section: "Grade 11 - Aristotle" },
      { name: "Krisha Marie Cabungcal", section: "Grade 11 - Aristotle" },
      { name: "Nechel Mae Cabungcal", section: "Grade 11 - Aristotle" },
      { name: "Samantha Dela Cerna", section: "Grade 11 - Aristotle" },
      { name: "Sweet Kiel Enad", section: "Grade 11 - Aristotle" },
      { name: "Kristel Erezo", section: "Grade 11 - Aristotle" },
      { name: "Angelie Espinosa", section: "Grade 11 - Aristotle" },
      { name: "Christ Jane Gabrillo", section: "Grade 11 - Aristotle" },
      { name: "Nikkie Lapina", section: "Grade 11 - Aristotle" },
      { name: "Merry Shane Lastima", section: "Grade 11 - Aristotle" },
      { name: "Shane Lauron", section: "Grade 11 - Aristotle" },
      { name: "Jhilia Mie Legarte", section: "Grade 11 - Aristotle" },
      { name: "Beverly Liniojan", section: "Grade 11 - Aristotle" },
      { name: "Therese Vincene Lumogda", section: "Grade 11 - Aristotle" },
      { name: "Kimberly Jane Mangubat", section: "Grade 11 - Aristotle" },
      { name: "Marie Cris Maputi", section: "Grade 11 - Aristotle" },
      { name: "Nikha Navacilla", section: "Grade 11 - Aristotle" },
      { name: "Chiecky Jayne Navarro", section: "Grade 11 - Aristotle" },
      { name: "Rona Navarro", section: "Grade 11 - Aristotle" },
      { name: "Maria Ivonne Regina Naveo", section: "Grade 11 - Aristotle" },
      { name: "Kisha Mae Navoa", section: "Grade 11 - Aristotle" },
      { name: "Fhebe Gail Pansan", section: "Grade 11 - Aristotle" },
      { name: "Kylla Parame", section: "Grade 11 - Aristotle" },
      { name: "Jermaine Denise Rafols", section: "Grade 11 - Aristotle" },
      { name: "Chelsea Ricaplaza", section: "Grade 11 - Aristotle" },
      { name: "Zairra Rudila", section: "Grade 11 - Aristotle" },
      { name: "Rhia Madjih Sabala", section: "Grade 11 - Aristotle" },
      { name: "Baby Jane Sasa", section: "Grade 11 - Aristotle" },
      { name: "Angie Satinitigan", section: "Grade 11 - Aristotle" },
      { name: "Ella Mae Tangaro", section: "Grade 11 - Aristotle" },
      { name: "Princess Samantha Tanilon", section: "Grade 11 - Aristotle" },
      { name: "Bhorly Aldaya", section: "Grade 11 - Socrates" },
      { name: "Kim Lee Dave Babao", section: "Grade 11 - Socrates" },
      { name: "John Emerson Babao", section: "Grade 11 - Socrates" },
      { name: "Kyle Andrey Bacalso", section: "Grade 11 - Socrates" },
      { name: "Klent Campugan", section: "Grade 11 - Socrates" },
      { name: "Renz Camuro", section: "Grade 11 - Socrates" },
      { name: "Louie Jay Cuizon", section: "Grade 11 - Socrates" },
      { name: "Nino Rey Escoto", section: "Grade 11 - Socrates" },
      { name: "John Lloyd Fernandez", section: "Grade 11 - Socrates" },
      { name: "Dominic Flores", section: "Grade 11 - Socrates" },
      { name: "Ivan Roy Lauron", section: "Grade 11 - Socrates" },
      { name: "Deejai Kyle Lauron", section: "Grade 11 - Socrates" },
      { name: "Roien Vince Lauron", section: "Grade 11 - Socrates" },
      { name: "Daniel Cane Sipalay", section: "Grade 11 - Socrates" },
      { name: "John Khyl Lausa", section: "Grade 11 - Socrates" },
      { name: "Cyrus Manayaga", section: "Grade 11 - Socrates" },
      { name: "Mark Ethan Maniego", section: "Grade 11 - Socrates" },
      { name: "Shane Mortifero", section: "Grade 11 - Socrates" },
      { name: "Elijah Vincent Pantilgan", section: "Grade 11 - Socrates" },
      { name: "Jahred Querubin", section: "Grade 11 - Socrates" },
      { name: "Zeanne Carlo Racoma", section: "Grade 11 - Socrates" },
      { name: "Raven Zach Rim", section: "Grade 11 - Socrates" },
      { name: "Vincent Sabala", section: "Grade 11 - Socrates" },
      { name: "June Jaren Saraum", section: "Grade 11 - Socrates" },
      { name: "Jemuel Satera", section: "Grade 11 - Socrates" },
      { name: "Rendy Satinitigan", section: "Grade 11 - Socrates" },
      { name: "John Lenard Siboco", section: "Grade 11 - Socrates" },
      { name: "Jerald Tangaro", section: "Grade 11 - Socrates" },
      { name: "Jhun Vergel Villaren", section: "Grade 11 - Socrates" },
      { name: "Vaughn Uriel Ybanez", section: "Grade 11 - Socrates" },
      { name: "Trisha Mae Aldaya", section: "Grade 11 - Socrates" },
      { name: "Cassie Zyrine Blanco", section: "Grade 11 - Socrates" },
      { name: "Rhosebhel Khay Borja", section: "Grade 11 - Socrates" },
      { name: "Jane Claire Cabungcal", section: "Grade 11 - Socrates" },
      { name: "Aira Mae Campana", section: "Grade 11 - Socrates" },
      { name: "Lady Jane Campugan", section: "Grade 11 - Socrates" },
      { name: "Princess Keziah Caparoso", section: "Grade 11 - Socrates" },
      { name: "Frencis Yancy Castanares", section: "Grade 11 - Socrates" },
      { name: "Nichole Kerstine Castanares", section: "Grade 11 - Socrates" },
      { name: "Trisha Rose Conley", section: "Grade 11 - Socrates" },
      { name: "Aveah Dayondon", section: "Grade 11 - Socrates" },
      { name: "Jade Althea Delgado", section: "Grade 11 - Socrates" },
      { name: "Christ Joy Gabrillo", section: "Grade 11 - Socrates" },
      { name: "Britney Blaze Lagarnia", section: "Grade 11 - Socrates" },
      { name: "Rachel Larrobis", section: "Grade 11 - Socrates" },
      { name: "John Nes Larrobis", section: "Grade 11 - Socrates" },
      { name: "Glyza Mae Larrobis", section: "Grade 11 - Socrates" },
      { name: "Alexa Lauron", section: "Grade 11 - Socrates" },
      { name: "Hanna Jency Lauron", section: "Grade 11 - Socrates" },
      { name: "Quency Bell Lausa", section: "Grade 11 - Socrates" },
      { name: "Chelsea Monacillo", section: "Grade 11 - Socrates" },
      { name: "Michaela Mae Monopollo", section: "Grade 11 - Socrates" },
      { name: "Hannah Keziah Oaper", section: "Grade 11 - Socrates" },
      { name: "Hannah Rucel Paldo", section: "Grade 11 - Socrates" },
      { name: "Gezel Myka Panugaling", section: "Grade 11 - Socrates" },
      { name: "Kris Jean Salcedo", section: "Grade 11 - Socrates" },
      { name: "Asia Gayle Santuyo", section: "Grade 11 - Socrates" },
      { name: "Glenndy Mae Satinitigan", section: "Grade 11 - Socrates" },
      { name: "Jennifer Tangkay", section: "Grade 11 - Socrates" },
      { name: "Mary Andrie Tapic", section: "Grade 11 - Socrates" },
      { name: "Trisha Mae Wamar", section: "Grade 11 - Socrates" }
    ];

    const input = document.getElementById('nameInput');
    const result = document.getElementById('result');

    input.addEventListener('input', function () {
      const query = input.value.toLowerCase().trim();
      if (!query) {
        result.textContent = "";
        return;
      }

      const student = students.find(s =>
        s.name.toLowerCase().includes(query)
      );

      if (student) {
        result.textContent = `${student.name} is in ${student.section}`;
      } else {
        result.textContent = "No match found.";
      }
    });
  </script>
</body>
</html>
