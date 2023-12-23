# masai-repo
 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Country Finder</title>
    <style>
        .country-card {
            border: 1px solid #ccc;
            padding: 10px;
            margin: 10px;
            width: 200px;
            display: inline-block;
            vertical-align: top;
        }

        img {
            max-width: 100%;
            height: auto;
        }
    </style>
</head>
<body>

<div>
    <label for="regionFilter">Filter by Region:</label>
    <select id="regionFilter" onchange="applyFilter()">
        <option value="all">All</option>
        <option value="Africa">Africa</option>
        <option value="Americas">America</option>
        <option value="Asia">Asia</option>
        <option value="Europe">Europe</option>
        <option value="Oceania">Oceania</option>
    </select>

    <label for="sortPopulation">Sort by Population:</label>
    <input type="checkbox" id="sortPopulation" onchange="applySort()">
</div>

<div id="countryContainer"></div>

<script>
    
    fetch('https://restcountries.com/v3.1/all')
        .then(response => response.json())
        .then(data => displayCountries(data));

    function displayCountries(countries) {
        const countryContainer = document.getElementById('countryContainer');
        countryContainer.innerHTML = '';

        countries.forEach(country => {
            const card = document.createElement('div');
            card.classList.add('country-card');

            card.innerHTML = `
                <h3>${country.name.common}</h3>
                <img src="${country.flags.png}" alt="${country.name.common} Flag">
                <p>Population: ${country.population}</p>
                <p>Region: ${country.region}</p>
                <p>Capital: ${country.capital}</p>
            `;

            countryContainer.appendChild(card);
        });
    }

    function applyFilter() {
        const regionFilter = document.getElementById('regionFilter');
        const selectedRegion = regionFilter.value;

        fetch(https://restcountries.com/v3.1/region/${selectedRegion})
            .then(response => response.json())
            .then(data => displayCountries(data));
    }

    function applySort() {
        const sortPopulationCheckbox = document.getElementById('sortPopulation');
        const sortPopulation = sortPopulationCheckbox.checked;


    }
</script>

</body>
</html>
