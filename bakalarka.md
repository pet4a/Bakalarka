#**Reengineering procesů** 

##**Teorie**
Tady bude teorie o reengineeringu 

##**Praktická část**

###**Připadová studie**

####**Problém**


človek kterej rentgen potrebuje schvaleni -> kontrola zda je rentgen v -> schvaleni ci odmitnuti [neresim]


###Analýza

K popisu budoucímu a stávajícímu řešení budeme používat notaci UML

#####**UML (Unified Modeling Language)**
V roce 1997 byla vytvořena první verze modelovacího jazyka UML. Je výsledkem sjednocení různých metod, syntaxí pro modelování. Jedná se o souhrn především grafických notací  k vyjádření analytických návrhových modelů. Umožňuje modelovat jednoduché i složité aplikace pomocí stejné formální syntaxe, a proto mohou být výsledky sdíleny s ostatními návrháři. UML je také jazyk pro vizualizaci, specifikaci, stavbu a dokumentaci softwarových systémů.

#####**CASE nástroje**
Jedná se o nástroje pro podporu analýzy a návrhu aplikací. V současnosti všechny ve světě rozšířené objektově orientované CASE nástroje vycházejí z modelovacího jazyka UML. Běžně užívané CASE nástroje jsou Rational Rose, Select Component Architect, PowerDesigner, AllFusion atd., Enterprise Architect

#####**Případy užití a testování**
Scénář případu užití je ideálním výchozím bodem pro tvorbu testovacích scénářů. Scénář případu užití vlastně definuje základní testovací požadavky na funkčnost budoucí aplikace. Je to sekvence kroků popisujících interakci mezi aktérem a systémem. Případ užití je sada scénářů, které spojuje dohromady společný cíl. V praxi je obvykle pravidlem, že případ užití má základní scénář typu "všechno šlo hladce" a řadu alternativních scénářů, které představují postup při zjištění různých chyb a mimořádných stavů.
_(KANISOVÁ, H. - MÜLLER M. UML srozumitelně. 1. vyd. 2004. ISBN 80-251-0231-9)_

#####**Use case diagram**(Diagram případů užití)
Umožňuje popsat chování systému z hlediska uživatele. V diagramu se specifikuje, jaké typy uživatelů používají systém a jaké činnosti vykonávají. Prvky diagramu jsou aktér (Actor), případ užití (Use Case) a vztah (Relation). 
**Aktér** reprezentuje prvek okolí systému, který komunikuje se systémem. Může to být jak živá osoba, hardwarové zařízení tak externí systém. Aktér se v UML označuje symbolem panáčka a názvem.
**Případ užití**(Use Case) specifikuje část funkcionality systému, kterou využívá aktér a která plní určitý cíl. Funkcionalita vyjádřená případem užití se realizuje jako posloupnost interakcí mezi aktérem a systémem. Tato posloupnost interakcí se označuje jako scénář případů užití. Jedná se o množinu možných scénářů. 
**Vztah** (Relation) mezi aktérem a případem užití vyjadřuje tok informace mezi vnějším prvkem (aktérem) a případem užití. Znázorňuje se čarou. 
_(BRUCKNER, T. et al. Tvorba informačních systémů. 1. vyd. 2012. ISBN 978-80-247-4153-6)_
        
Kromě vztahů mezi případy užití a aktéry můžeme identifikovat také několik druhů vztahů mezi případy užití samotnými. Jedná se o tyto vztahy:

 - relace include tam, kde existuje podobná nebo stejná část sekvence scénáře, opakující se ve více případech užití, není vhodné udržovat více kopií shodných částí scénářů, základní případ užití není bez rozšiřujícího případu užití kompletní 
 - generalizace případů užití - umožňuje chování společné pro více případů užití převést do rodičovského případu užití, ovšem zvyšuje nepřehlednost modelu
 - relace extend - přidává rozšiřující případ užití - nové doplňkové chování do základního případu užití, oproti relaci include je případ užití sám o sobě zcela soběstačný, modeluje volitelné části, základnímu scénáři je jedno, kdo ho rozšiřuje
_(KANISOVÁ, H. - MÜLLER M. UML srozumitelně. 1. vyd. 2004. ISBN 80-251-0231-9)_


zadavatel [actor] -> zaznamenání změřených hodnot 
vedouci [actor] -> jednou za měsíc vygeneruje protokol ze záznamu do pdf
vedoucí [actor] -> vyhledávání v datech 

####**Sběr požadavků** *z toho vyextrahuju analýzu, popis stávající situace*

**1, Popis stávající situace**
 Puvodní řešení založeno na zapisován záznamů do MS Excel

Výhody | Nevýhody
------------ | -------------
Všeobecná uživatelská znalost | Není validace dat (možnost překlepu)
Velmi jednoduchá manipaluce (zadávání) | Chybí Auditing (Kdo co kdy změnil)
Stačí pouze jeden SW | Historizace (Změna dat v čase)
Stejný interface | Neexistence zálohování
Všichni to znaj | Nulové zabezpečení (kdokoliv kdo má přístup na pc muže smazat celý soubor (z důvodů že není soubor umístěn na sdíleném disku)
|| Na dokumentu nemuže pracovat více lidí současně
|| V případě přenesení souboru jinam není zaručena jejich aktuálnost



**2, Návrh řešení ** 
Po zhodnocení následující analýzy, kdy některé z těchto problémů se dají řešit pomocí různých způsobů, které se liší dle složitosti realizace. [TODO: ta veta mi nedava smysl, bud bych ji uplne smazal nebo nejak prepsal, u krabicoveho reseni bych napsal ze na takovyhle spcificky problem zadny SW produkt nebude existovat]

1. Zachování stávajícího SW a změna způsobu použití
    * Přenesení soboru na sdílený disk
    * Nastavení funkce sdílení (podívat se do officu na funkci sdílení)
    * Nastavení zálohování        
2. Krabicové řesení http://knihy.cpress.cz/softwarove-inzenyrstvi.html#
3. Vlastní SW 

  Výhody | Nevýhody
------------ | -------------
řešení všech nevýhod | časová náročnost implementace
                                   || nekdo musi SW spravovat (nasazovani, udrzba serveru)
                                   || nekdo musi resit chyby (maintanance - udrzba)
                                     

    
**3 výběr řešení**
Pro účely bakalářské práce jsem se rozhodl vyřešit všechny stávající negativa vývojem SW na klíč.

**4, Vývoj**

  
 1. Metodika vývoje
Metodiky vývoje aplikací jsou jedněmi z nejdůležitějších produktů softwarového inženýrství. Cílem bylo se vždy přizpůsobit konkrétním požadavkům kladeným na software v dané době a odstranit nedostatky vývoje aplikací. Dnešní - agilní - metodiky se pokouší vést vývoj tak, aby výsledný produkt byl dodán co možná nejdříve. Rychlost je jedním ze základních požadavků na vývoj softwaru v dnešní době.
Jednotlivé metodiky:
- Metodika napiš a oprav - prvopočátek vývoje programů (50. léta 20. století) - model spočíval v sepsání aplikace, následném předání do provozu a v opravování chyb
- Striktní posloupnost fází - (r. 1957) tzv. stagewise model žignotního cyklu (definice problémů, specifikace požadavků, architektura a návrh, implementace, integrace, provoz), problémem byla naprostá absence jakékoliv zpětné vazby
- Vodopádový model - (v 70. letech) od svého předchůdce stagewise modelu se liší především snahou o jakousi zpětnou vazbu
- Spirálový model - (r. 1985) reagoval na některé nedostatky vodopádového modelu, zavádí dva inovativní koncepty (iterativní přístup - vývoj aplikace v opakovaných krocích a opakovanou analýzu rizik)
- Další modely - z vodopádového modelu dále vznikly např. Test Development, Exploratory Programming, Prototyping Model, Transformation Model, dále v 70.  letech Yourdonova metodika,  v 80. letech SSADM, v 90. letech první zástupce prostorově orientovaných metodik např. Rational Unified Process
- začátkem 3. tisíciletí - agilní metodiky - extrémní programování (XP), TDD (Test Driven Development - vývoj řízen testy), Crystal, SCRUM, LEAN atd. - metodiky umožňující co nejrychlejší vývoj softwaru, jeho průběžnou údžbu a reakci na měnící se podmínky a zadání
_(KADLEC, V. Agilní programování. 1. vyd. 2004. ISBN 80-251-0342-0)_  
- prototypy **DOPSAT** zdroj: https://www.cms.gov/research-statistics-data-and-systems/cms-information-technology/xlc/downloads/selectingdevelopmentapproach.pdf
**DOPSAT Zvolení metodiky a proč**
![Obrázek prototyping](https://raw.githubusercontent.com/pet4a/Bakalarka/master/Obr%C3%A1zky/Prototyping.bmp)
  
 2. Softwarová architektura
V případě softwarové architektury je systémem, na kterém architekturu definujeme, jeden softwarový produkt, tedy jedna softwarová aplikace. Hlavními komponentami, jejichž strukturu a vztahy architektura definuje, jsou programové moduly aplikace.
    
 **Klient / server architektura **- V klient/server architektuře je aplikace rozdělena na dva nebo více kooperujících programů. Klientem je ten program, který vyžaduje provedení určité služby (funkcionality), zatímco serverem je ten, který danou službu na požádání poskytuje. Jeden a tentýž program přitom jednou může vystupovat jako klient, jindy jako server. Klient i server mohou být umístěny buď na tomtéž počítači, nebo mohou pracovat na různých počítačích počítačové sítě.  
    
    Výhody | Nevýhody
 ------------ | -------------
 nižší nároky na server oproti centralizovanému zpracování (část zátěže nese klient) | vyšší počáteční investice pro zprovoznění aplikací
snadnější inkrementální růst kapacit - vhodné zejména u víceuživatelských aplikací, kde klient řeší zpracování uživatelského rozhraní, s růstem počtu uživatelů roste počet koncových stanic, ale nároky na server rostou jen minimálně | problémy s integrací různých platforem
lze zvolit zvlášť vhodnou provozní platformu pro jednotlivé části aplikace | vyšší nárok na kvalifikaci řešitelů
snadnější zabezpečení ochrany dat pomocí specializovaného datového serveru||
 Dělení softwarové architektury: **monolitická**, **dvouvrstvá** a **třívrstvá**.

 **Klient/server** architektura se aplikuje v dvou- a třívrstvé softwarové arhitektuře.
Aplikace obvykle obsahuje tři základní skupiny funkcí: 
* datové
* věcně orientované funkce
* komunikační funkce

 Základní rozdíl mezi monolitickou, dvouvrstvou a třívrstvou architekturou je v tom, zda jsou tyto skupiny funkcí odděleny do samostatńých programů, či nikoliv. Monolitická architektura je typická pro centralizované zpracování. Tři skupiny funkcí jsou vzájemně propleteny a program běží na jednom počítači. U dvouvrstvé architektury jsou možné dvě varianty řešení aplikace - tzv. tlustý klient nebo tenký klient - viz. obrázek. Obě varianty sledují hlavní cíl - oddělit komunikační a datové funkce aplikace. Třívrstvá aplikace umožňuje každou ze skupin funkcí udržovat a rozvíjet zcela samostatně, pro každou z nich je také možné zvolit nejvýhodnější vývojové a provozní prostředí. Je ideální pro tvorbu otevřených, distribuovaných a flexibilních informačních systémů.
_(BRUCKNER, T. et al. Tvorba informačních systémů. 1. vyd. 2012. ISBN 978-80-247-4153-6)_
 
 3. Vývojové nástroje
**IDE vs textový editor vs programátorský textový editor**

 **IDE**
Integrované vývojové prostředí (IDE) je softwarová sada, která slučuje základní nástroje pro vývojáře k psaní a testování software. Typicky, IDE obsahuje editor kódu, kompilátor nebo interpret a debugger, kam vývojář přistupuje prostřednictvím jednotného grafického uživatelského rozhraní (GUI). IDE může být samostatná aplikace, nebo může být součástí jednoho či více existujících a kompatibilních aplikací. **(1)** IDE dále může obsahovat:
- automatické dokončování kódu
- přístup k databázím
- optimalizace
- řízení verzí 

 Mezi nejznámější IDE patří IntelliJ, Eclipse, Visual Studio, NetBeans, Komodo a BlueJ

 **Textový editor**
Textový editor je program, který umožňuje otevírat, zobrazovat a upravovat textové soubory. Na rozdíl od textových procesorů, textových editor nepřidává formátování textu, místo toho se zaměřuje na editační funkce pro prostý text.**(2)**
Např. Microsoft Notepad, TextEdit


 **Programátorský textový editor**
Jsou to textové editory, které jsou vyrobeny speciálně pro použití programovacích jazyků. Z důvodů odlišení se nazývají programátorské textové editory, ale většinou se jím říká pouze textové editory. Stále se zabývají pouze textovými soubory, ale mají také některé užitečné funkce pro programátory **(3)**: 
- zvýrazňování syntaxe ( pravidla pro zápis formálního jazyka )
- automatická editace kódu
- kompilační a spouštěcí příkazy 

 Např. Atom, UltraEdit, Sublime Text, Visual Studio Code, Text Mate, emacs, vim ...
 Pro porovnání jednotivých IDE a textových editorů je možné použit webové srovnání na adrese www.vschart.com


 Pro účely této bakalářské práce jsem si vybral programátorský textový editor, konkrétně Sublime Text, mezi jeho výhody patří velké množství open source pluginů, náhled kódu, nastavitelnost a přehlednost. Přestože Sublime text není poskytován zdarma, je možnost neomezeně používat jeho zkušební verze, která je k dispozici na oficiálních stránkách autora www.sublimetext.com


 Zdroje
1. http://searchsoftwarequality.techtarget.com/definition/integrated-development-environment
2. http://www.text-editor.org/
3. http://java.about.com/od/gettingstarted/a/ideversuseditor.htm

 4. Použité technologie
 Řešení budu realizovat jako webovou aplikaci. Server bude tvořit kód v jazyce PHP komunikující s databázi MySQL.
 Klientská strana (GUI) bude tvořena standardní kombinací HTML (text a struktura), CSS (stylovací jazyk) a jazykem JavaScript (např. validace dat na klientovy, před odesláním na server)
 
 Důvody:
**PHP**
- dobře dokumentovaný
- velká rozšířitelnost
- velká komunita (je snadné najít řešení problému)
- snadné nasazení
- rychlost vývoje 

 **Javascript** 
  z důvodu uživatelské přívětivosti UX - user experience (Validace na straně klienta), podpora většiny webových prohlížeču.
**jQuery**
  nejrozšířenější knihovna (znovupouželný kód) pro Javascript
**MySQL**
        Současná infrastruktura, kam se bude SW nasazovat již používa toto SŘBD

     
 5. implementace:
a) návrh obrazovek (prototyp)
Návrh ukázat uživatelům=>zpětá vazba=>případné změny=>návrh ukázat uživatelům

 zvažuju technickou náročnost řešení
 
 b) skutečná implementace

  
  2. grafický návrh
  3. kód
   AJAX
  PDO - používá se sql - nezávislost na použitém SŘBD (pouze malá nebo žádná úprava dotazu)
  - Export do PDF
                  mPDF
                  _https://mpdf.github.io/_
  
  3. persistentní vrstva [db] nějaký zdroj
  Normativní formy
       ER model [koncepční model] doplnění až bude vymyšlenej table user, option, auditing
  **obrázek**
 fyzicky model
 **obrázek**
 Kardinality

                
  4. Autorizace a autentizace   SESSION?
     
      aplikace není veřejně přístupná - proč autentizuju
      admin-kdo co
      uzivatel- kdo co
       
   autentizace SESSION
           
  5. Bezpečnost (owasp top ten)
   rozepsat všech deset owasp - a jak je řeším
   SQL injection - co to je? a jak se bránit
   
  6. Auditing (Kdo co kdy) Obecné info
Proč auditing, 
Historizace

  
  7. Správa verzí
Správa verzí je systém , který zaznamenává změny souboru nebo sady souborů v průběhu času, a uživatel tak může kdykoli obnovit jeho/jejich konkrétní
verzi (tzv. verzování)**(1)**. Jako systém správy verzí jsem si vybral Git, což je jeden z nejvíce používaných verzovacích systémů. V mém soukromém repozitáři jsem zaznamenával nejenom verze mojí webové aplikace, ale i postupnou tvorbu této bakalářské práce. Bakalářská práce byla kvůli snadnějšimů čtení převedena do jazyka Markdown (Nástroj pro webové vývojáře sloužící pro převod prostého textu na strukturálně validní XHTML nebo HTML)**(2)**
   
     Zdroje:
     1. CHACON, Scott. Pro Git. Praha: CZ.NIC, c2009. CZ.NIC. ISBN 9788090424814. Dostupné také z: http://kramerius.mzk.cz/search/handle/uuid:08825630-78a3-11e5-99af-005056827e52 
        2. Daring FireballL: Markdown. Daring FireballL: Markdown [online]. [cit. 2016-10-16]. Dostupné z: http://web.archive.org/web/20040402182332/http://daringfireball.net/projects/markdown/

  8. Testování
manuální testování případně další metody testování
proč to testovat - obecné info
jak to testovat 
jaké jsou možnossti
zkontrolat jestl je to testování nebo jiná technika QA
     Metody:
     
     **Revize partnerem**
     revize partnerem se často provádí pouze s programátorem, který posuzovaný kód napsal, a s jedním nebo dvěma dalšími programátory či testery, kteří fungují jako oponenti. Tato malá skupina reviduje programový kód zpravidla společně a hledá v nněm problémny a přehlédnuté věci.


     **Průchody** (procházení, walkthrough) 
Průchody kódu jsou dalším krokem ve zvýšení formálnosti oproti partnerským revizím. Při průchodu kódem prezentuje programátor svůj vlastní kód malé skupině zhruba pěti dalších programátorů a testerů. Oponenti (recenzenti) dostanou kopii softwaru s předstihem před vlastní revizí a mohou jej tak samostatně a prozkoumat a napsat si komentáře a otázky, které budou chtít při revizi přednést. 
Překladatel (autor kódu) čte řádek za řádkem nebo funkci za funckí a postupně vysvětluje, co která část kódu dělá a proč. Oponenti mu naslouchají ihned e ptají na cokoliv, co se jim zdá podezřelé.**(1)**     


     Zdroje:
     1. PATTON, Ron. Testování softwaru. Vyd. 1. Praha: Computer Press, 2002. Programování. ISBN 80-7226-636-5.


9. migrace stavajicich dat 
  
- čištění - základní info, popsat problémy a poléze jejich řešení
- nahrání
mysql connector
_http://dev.mysql.com/doc/mysql-for-excel/en/_




 6. Dokumentace
        I. programátorská příručka
          jak to zprovoznit
          konvence - facebook php konvence - možná jiný, zkusit najít
          co je v jakém souboru
       II. uživatelská příručka


####Poznámky
Návrh řešení (client server architektura, serverová část PHP na Apache HTTP server, klientská část v prohlížeči JS (jQuery), komunikace pomocí HTTP) 


####Zkratky
 VCS - Version control systems (systém správy verzí)
 SŘBD - systém řízení báze dat  
 DB - databáze  
 JS - javascript  
 AJAX - asynchronous JavaScript and XML  
 GUI - Graphical unit interface, grafické uživatelské rozhraní  
 ER model - Entity-relationship model - entitově vztahový model  
 PDO - PHP Data Object  
 UX - user experience 


####Zdroje
 Softwarové inžeýrství - Ian Sommerville  
 Agilní programování  
 Destilované UML  
 UML  
 OWASP Top ten  
 Návrh databáze - rozdělení databází, výhody, nevýhody  
 php.net devbook  
 w3schools.com  
 Kniha AJAX  
 Use Case??  
 Dokumentace 
 jQuery  
 Něco o migraci dat  