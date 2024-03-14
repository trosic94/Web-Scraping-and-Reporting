
U ovom repozitorijumu vam se nalazi skeleton docker nodejs aplikacije koji ce vam biti pocetna tacka.

1.  Doraditi aplikaciju tako da preuzima live korisnička imena igrača sa Stake.com i smešta ih u tabelu stake_players relacione baze podataka.
    Username-ovi igraca se pojavljuju na kartici "All bets".
2.  Napisati SQL kojim se moze pratiti koliko se username-ova pojavljuje u poslednjih sat vremena.
3.  Napisati SQL koji pokazuje u poslednih 10h koliko je username-ova bilo po satu.
    Npr.:
    
        |  Broj usera  | Hour
        |      15      | 14:00
        |       8      | 15:00
        |       3      | 16:00
        |       ...    | 17:00
    
Za resavanje prva 3 zadatka vam je potrebna sledeca tabela:: 
stake_players(username, date) - date kolona predstavlja trenutno vreme koje je potrebno za realizaciju trazenih sql-ova, kolona username je primary key
4. Napisati paralelnu funkciju koja ce za preuzete stake igrace proveravati da li se neki od username-ova nalazi kod konkurentskih sajtova (shuffle i gamdom), ukoliko se nalazi preuzeti njihov wager sa konkurentskih sajtova i upisati u drugu tabelu.
    Da bi ste scrape-ovali wager igraca sa drugih sajtova mozete koristiti web scraping sa frontend-a ili pronadjite public API koji vraca ove podatke. 
    
Za 4. zadatak potrebna je sledeca tabela:
stake_competitors_players (username, competitor_name, wager,date): competitor_name kolona je naziv konkurencije  SHUFFLE ili GAMDOM, wager kolona je NUMERIC polje i oznacava koliko je igrac wagerovao kod konkurencije. Foreign key je username iz tabele stake_players.


## Tehnologije koje se koriste:

- PostgreSql - ili neka druga SQL baza podataka.
- NodeJs
- Puppeteer - ili neki drugi lib za web scraping
- Sequelize(ORM) - nije obavezno koristiti ORM, mozete i plain sql.

## Preduslovi:

Da biste počeli sa projektom, potrebno je instalirati Docker Desktop i Node.js(uz koji dolazi NPM).

## Instalacija:

1. Instalirajte Docker Desktop sa [zvanične web stranice](https://www.docker.com/products/docker-desktop).
2. Instalirajte Node.js sa [zvanične web stranice](https://nodejs.org/).
3. Za pisanje SQL-a i upravljanje bazom podataka mozete koristiti tool na koji ste navikli, moja preporuka je dbeaver.
    Konekciju za bazu vam se nalaze u docker-compose.yml fajlu.

## Uputstvo za instalaciju:

1. Klone ovaj repozitorijum: `git clone git@github.com:trosic94/Web-Scraping-and-Reporting.git`
2. Uđite u direktorijum projekta: `cd repozitorijum`
3. Pokrenite Docker Desktop.

## Uputstvo za korišćenje:

1. Pokrenite aplikaciju pomoću `docker-compose up`.
