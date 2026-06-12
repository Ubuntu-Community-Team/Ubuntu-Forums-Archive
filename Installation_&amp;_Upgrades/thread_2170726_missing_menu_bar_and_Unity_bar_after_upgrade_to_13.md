---
title: "missing menu bar and Unity bar after upgrade to 13.04"
date: 2013-08-27
forum: Installation &amp; Upgrades
---

### Post by rafal311 on 2013-08-27
Hello all,

I've recently updated my ubuntu system from 12.04 to 12.10 and directly after that to 13.04 and now I got into trouble :mad:.
I miss the main menu and the left Unity bar. 

I already had same problem after update to 12.10 but that helped:
> 
sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-legacy


after update to 13.04 same problem appeared but the above solution didn't helped :(.

I also tried some other ones:
- reinstalling the ATI drivers described on many pages
- resetting the uniy  like described in those link [http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04](http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04)

Nothing helped :/
It seems that it's now worse then on the beginning. when I'm trying to use the first solution (see quotation) i get those errors:

> 
xxx@xxx:~$ sudo apt-get install fglrx-legacy
[sudo] password for rafal: 
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Zostan&#261; zainstalowane nast&#281;puj&#261;ce NOWE pakiety:
  fglrx-legacy
0 aktualizowanych, 1 nowo instalowanych, 0 usuwanych i 0 nieaktualizowanych.
2 nie w pe&#322;ni zainstalowanych lub usuni&#281;tych.
Konieczne pobranie 0 B/66,5 MB archiwów.
Po tej operacji zostanie dodatkowo u&#380;yte 8192 B miejsca na dysku.
(Odczytywanie bazy danych ... 271652 pliki i katalogi obecnie zainstalowane.)
Rozpakowywanie pakietu fglrx-legacy (z .../fglrx-legacy_2%3a8.97.100.7-makson1~raring3_amd64.deb) ...
One or more files have been altered since installation.
Uninstall will not be completed. See /etc/ati/fglrx-uninstall.log for details.
dpkg: b&#322;&#261;d przetwarzania /var/cache/apt/archives/fglrx-legacy_2%3a8.97.100.7-makson1~raring3_amd64.deb (--unpack):
 podproces nowy skrypt pre-installation zwróci&#322; kod b&#322;&#281;du 1
Brak raportu programu apport, poniewa&#380; osi&#261;gni&#281;to limit MaxReports
                                                                  Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 /var/cache/apt/archives/fglrx-legacy_2%3a8.97.100.7-makson1~raring3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


System:
Ubuntu 13.01
laptop: compal khlb2
ATI Mobility Radeon HD 4650 &#8211; 512 MB
Intel Core 2 Duo T9400 2.53 GHz

I'm waiting for your support.

BR
Rafal

---

### Post by rafal311 on 2013-08-28
Nobody who could help :(?

---

### Post by grahammechanical on 2013-08-28
You could try changing the video driver but how can you do that when you cannot open System Settings? Right click the desktop background image. Does a menu appear? Select Change Desktop Background. That will open the Appearance menu which is part of System Settings. Click All Settings and then load Software and Updates and open the Additional Drivers tab. Wait a few minutes while the utility searches for drivers and then experiment.

As you have worked out for yourself, it is a video driver issue. 

Regards.

---

### Post by rafal311 on 2013-08-28
[COLOR=#222222][FONT=Verdana]I've fixed it :) [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]how?to be honest, hard to say :/.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]ButI will try to describe all the done steps.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]1.I've fixed the [/FONT][/COLOR][FONT=Verdana]fglrxproblem in the packages. (like recommended by apt-get)
2. commandas root: "unity-reset"
3. [/FONT][FONT=Verdana]commandas root: "unity"
And the menus are back :) 
butafter restart not the problem reappeared...
4. do step 2,3 asstandard used restart
5. again same like 4 (hot restart - computer[/FONT][FONT=Verdana]freezes[/FONT][FONT=Verdana])
6.after restart unity is there again :) 
DONE

maybe by[/FONT][FONT=Verdana]accident[/FONT][FONT=Verdana]but working[/FONT]

---

### Post by Tomasz_Piechota on 2014-02-20
> **rafal311 said:**
> Nobody who could help :(?

Try:
...$ sudo apt-get install compizconfig-settings-manager
...$ ccsm

in the manager window go to Preferences (left pane) in the profile section select "unity" instead of "Default" in the drop-down menu.

You may also want to:
retick OpenGL and enable Ubuntu Unity Plugin in Ubuntu Unity Plugin option.

Hope it helps.

Worked for me :)

---

