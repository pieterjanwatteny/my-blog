---
layout: post
title: "Salesforce + Amazon Connect Tutorial"
date: 2021-03-28 13:30:00 +0100
categories: Blogpost
author: Pieter-Jan Watteny
awsSF: /assets/images/awsSF.jpg
step1: /assets/images/step1.jpg
step2: /assets/images/step2.jpg
step3: /assets/images/step3.jpg
step4: /assets/images/step4.jpg
step5: /assets/images/step5.jpg
step6: /assets/images/step6.jpg
step7: /assets/images/step7.jpg
step8: /assets/images/step8.jpg
step9: /assets/images/step9.jpg
step10: /assets/images/step10.jpg
step11: /assets/images/step11.jpg
step12: /assets/images/step12.jpg
step13: /assets/images/step13.jpg
step14: /assets/images/step14.jpg



---
![Aws+Salesforce]({{page.awsSF | relative_url}})
# Onderzoek, wat is Amazon Connect

Hoe kom ik tot de beslissing om een tutorial te schijven over de integratie van Salesforce en Amazon Connect?
Voor mijn bachelor proef onderzoek ik de implementatie van telefonie (CTI) in Salesforce, hiervoor heb ik vele verschillende services onderzocht, en bevraagt. Meestal is er een probleem vanaf je duidelijk maakt dat je een student bent die onderzoek uitvoert in het onderwerp. Zoals je wel kan begrijpen is dit voor de verstrekkers van Cloud Telefonie niet echt interessant om veel tijd hierin te steken, (dit laten sommige toch duidelijk blijken). Maar bij deze wil ik de personen waarmee ik in contact kwam die mij hebben kunnen helpen via een Demo of Webinar alvast bedanken.

Desondanks dat Amazon Connect niet de meest ideale CTI-integrator is in Salesforce voor Belgische bedrijven heb ik er toch voor gekozen om via deze tutorial te tonen hoe zo een integratie in zijn werk gaat. De reden dat ik dus gekozen hem voor een tutorial met als onderwerp Amazon Connect is omdat dit iets is die relatief gemakkelijk kan worden opgezet en effectief functioneel bruikbaar is.
## Implementatie van CTI via Amazon Connect

### Nu Hoe start je met het opzetten van Amazon Connect ?

#### Stap1
Om te beginnen dien je een Salesforce omgeving op te zetten, bij voorkeur vraag je een development omgeving aan als je geen toegang hebt tot een productie of sandbox omgeving.

![Stap1 ]({{page.step1 | relative_url}})

#### Stap 2
Vervolgens dien de CTI adapter te installeren in je eigen omgeving via de Appexchange van Salesforce. [Amazon Connect CTI Adapter]( https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3A00000EJH4yUAH)

![Stap2 ]({{page.step2 | relative_url}})

je kan controleren of dit volledig goed is verlopen door te gaan kijken in de Setup van de Salesforce omgeving onder installed Packages en daar zou je de Amazon Connect packge moeten zien staan 

![Stap3 ]({{page.step3 | relative_url}})

#### Stap 3 
Nu zal je Acces Permissions moeten definiëren in Salesforce 
deze vind je terug in de Setup onder Permission Set. Hier zal je enkele nieuwe permission sets zien die je moeten toewijzen aan de users die gebruiken moeten maken van de Amazon Connect Plugin.
![Stap4 ]({{page.step4 | relative_url}})


#### Stap 4
Hierna dien je de Service Console aan te passen via de App Builder en er de Utility ‘Phone’ als Open CTI Softphone toe te voegen aan de lijst met Utility Items.
![Stap5 ]({{page.step5 | relative_url}})

#### Stap 5
Vervolgens dien je het Visual force component in te stellen 
dit doe je door terug via de Setup in je Salesforce dev org naar  Visualforce Pages te gaan en daar te kiezen voor de amazonconnect__AC_LinghtningAdapter. Eens je deze hebt geselecteerd kies je voor de Preview knop bovenaan en deze opent een externe tab waar je enkele de login knop van het Amazon Contact Control Panel zal te zien krijgen. Kopieer de URL van deze pagina want deze is uniek en heb je nodig in de volgende stappen.

![Stap6 ]({{page.step6 | relative_url}})

De volgende stappen zullen zicht plaatsvinden op het AWS platform.

#### Stap 6
Je zal eerst een AWS account moeten aanmaken, hiervoor dien je in bezit te zijn van een creditkaart aangezien dit een verplichting is om een account aan te maken. Verder zijn er geen vereisten.

#### Stap 7
Vervolgens zal je naar de Amazon Connect service die je vindt via de searchbar.
Eens je aankomt in de Amazon Connect service zal je een instance moeten aanmaken.
![Stap7 ]({{page.step7 | relative_url}})


Dit gebeurt aan de hand van een kort stappenplan waar je de admin user aanmaakt en de acces url en alias beslist van uw instantie. Ook zal je moeten selecteren of je gebruik wil maken van zowel inbound als Outbound telefoonverkeer. 

![Stap8 ]({{page.step8 | relative_url}})
#### Stap 8
Eens deze is aangemaakt selecteer je instance en ga naar de menu Approved origins,
hier voeg je de URL links toe van je Setup omgeving van de Salesforce Dev org als van je Visualforce element (waar je op preview duwde) zie stap 5. Alles na .com kan worden wegelaten

![Stap9 ]({{page.step9 | relative_url}})
#### Stap9
Terug in Salesforce
Nu zul je het Callcenter gebeuren aanpassen om de basis installatie te vervolledigen en wat functionaliteit te voorzien in SF zelf. In je Dev org ga terug via de Setup naar Call centers onder Services.

![Stap10 ]({{page.step10 | relative_url}})

Klik op continue als je het venster ziet ‘Say Hello to Salesforce Call center’ en selecteer AC Lightning Adapter en klik op edit . Vervang ook hier terug onder General Information de URL van het AC lighning adapter visualForce element zoals op stap 5 en stap 8.
Je het is aangeraden om ook de Softphone height aan te passen naar 570 en de width naar 330 om zo de adapter beter te laten ‘passen’ .

![Stap11 ]({{page.step11 | relative_url}})


#### Stap 10
Vervolgens keer je terug naar de AC Lightning Adapter en kies je Manage Call Center Users. 
Hier voeg je terug de users toe die gebruik zullen maken van het Callcenter. Vergeet jezelf dus zeker niet toe te voegen als admin!



#### Stap 11
We zijn er bijna 😊 
In de quick find bij Setup heef je in Custom settings en kies je dan de Toolkit for Amazon Connect.
Klik op Manage -> New en dan kom je op volgend scherm: 

![Stap12 ]({{page.step12 | relative_url}})![Stap12 ]({{page.step12 | relative_url}})

Voeg hier de URL van de Amamazon connect instance toe die je aanmaakte in stap 7.
Nu is je Amazon connect instantie en je Salesforce dev org volledig verbonden met elkaar en is de basis setup klaar voor gebruik. Maar we voegen nog een iets toe om wat functionaliteit te halen uit deze implementatie namelijk de Screen pop. Dit gebeurt door het configureren van Softphone Layouts


#### Stap 12
Heef in de Setup in de quick find in ‘Softphone’ en selecteer de Softphone Layouts.
De kans bestaat terug dat je een ‘welcome’ scherm krijg, klik op continue.
Selecteer New en maak een DefaultLayout aan, in dit voorbeeld noemen we hem ‘ AmazonConnectDefault’. Vergeet deze niet als default de selecteren door deze ‘Is default layout’ checkbox aan te likken. 

![Stap13 ]({{page.step13 | relative_url}})

Eens aangemaakt om je in een menu terecht voor deze layout en kan je deze configureren zoals je zelf wenst. Wij zullen kiezen voor ‘Inbound’ bij de Select Call Type bovenaan en vervolgens bij de screen pop settings kiezen we in ons voorbeeld als er een gebeld wordt met een bestaand telefoon nr dus ‘ Single- Matched record dat de detail page van die related getoond wordt. 
Eens je dit geselecteerd hebt druk op Save.
En zo heb je zopas een basis integratie gedaan van Amazon Connect in Salesforce.
Hieronder zie je dan een voorbeeld van hoe dit eruit ziet een je een contact opbelt en je op ‘ available’ staat in de Phone utility in de Service Console van je Salesforce Development org.

![Stap14 ]({{page.step14 | relative_url}})