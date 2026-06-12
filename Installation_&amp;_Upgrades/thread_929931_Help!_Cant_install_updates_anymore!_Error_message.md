---
title: "Help! Cant install updates anymore! Error message"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by jannen on 2008-09-25
Dear all

**Please could someone help me. My ubuntu 7.10 always started to give an error when I try to install updates (cant install anything at moment!):**

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
[B]

When I run the "sudo dpkg --configure -a" I get this response:[/B]

Setting up libxml2-utils (2.6.31.dfsg-2ubuntu1.2) ...
Setting up deskbar-applet (2.22.3.1-0ubuntu1) ...

(gconftool-2:6747): GConf-CRITICAL **: Failed to load file "/var/lib/gconf/defaults/%gconf-tree-eu.xml": Error on line 5836 char 54: '<' is not a valid character following the close element name 'en'; the allowed character is '>'
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 70, in <module>
    shutil.rmtree(tmp_home)
  File "/usr/lib/python2.5/shutil.py", line 178, in rmtree
    onerror(os.rmdir, path, sys.exc_info())
  File "/usr/lib/python2.5/shutil.py", line 176, in rmtree
    os.rmdir(path)
OSError: [Errno 30] Read-only file system: '/tmp/gconf-rQBQCt'
dpkg: error processing deskbar-applet (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: error processing compiz-fusion-plugins-main (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up rdesktop (1.5.0-3+cvs20071006ubuntu0.1) ...
dpkg: error processing rdesktop (--configure):
 unable to flush updated status of `rdesktop': Read-only file system
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted

**Nothing happens.. please help me to sort this out! Thanks!!! :(**

---

### Post by Elfy on 2008-09-25
At a guess I would say that there is something wrong with the .xml file.

Have you opened it to see if it makes any sense

```
gedit /var/lib/gconf/defaults/%gconf-tree-eu.xml
```

If you go to preferences you can enable line numbering which will make it a bit easier to find line 5836 :)

I am not sure the following errors are caused by the problem in the xml file.

---

### Post by jannen on 2008-09-25
**Line 5836 get this stuff: No idea what this stands for! (and why its not in english...) any idea where to go next?**


 <dir name="deskbar">
                                <entry name="ui_name">
                                        <local_schema short_desc="Erabiltzailearen interfazea hautatzen du erabiltzeko, &quot;Window&quot; edo &quot;Button&quot; izan daiteke.">
                                        </local_schema>
                                </entry>
                                <entry name="max_history_items">
                                        <local_schema short_desc="Historian gordetako gehienezko elementuen kopurua">
                                        </local_schema>
                                </entry>
                                <entry name="hide_after_action">
                                        <local_schema short_desc="Leihoa itxi ondoren ekintza aktibatzen den ala ez">
                                                <longdesc>Gaitzen bada leihoa itxi egingo da ekintza bat aktibatutakoan</longdesc>
                                        </local_schema>
                                </entry>
                                <entry name="window_y">

**etc...**

---

### Post by Elfy on 2008-09-25
It's the foreign bit of the file mine is similar - is that the whole line? You need to find char 54 -

If that is not just line 5836 then post just the one line.

---

### Post by jannen on 2008-09-26
**Hi there... I tried to find any problem on the line 5836... didnt spot anything weird. Mind helping? This is the whole rest of the script - first line is 5836**
[SIZE="2"]
                        <dir name="deskbar">
                                <entry name="ui_name">
                                        <local_schema short_desc="Erabiltzailearen interfazea hautatzen du erabiltzeko, &quot;Window&quot; edo &quot;Button&quot; izan daiteke.">
                                        </local_schema>
                                </entry>
                                <entry name="max_history_items">
                                        <local_schema short_desc="Historian gordetako gehienezko elementuen kopurua">
                                        </local_schema>
                                </entry>
                                <entry name="hide_after_action">
                                        <local_schema short_desc="Leihoa itxi ondoren ekintza aktibatzen den ala ez">
                                                <longdesc>Gaitzen bada leihoa itxi egingo da ekintza bat aktibatutakoan</longdesc>
                                        </local_schema>
                                </entry>
                                <entry name="window_y">
                                        <local_schema short_desc="Leihoaren Y koordenatua">
                                                <longdesc>Leihoaren posizio lehenetsia pantailan (y koordenatua)</longdesc>
                                        </local_schema>
                                </entry>
                                <entry name="window_x">
                                        <local_schema short_desc="Leihoaren X koordenatua">
                                                <longdesc>Leihoaren posizio lehenetsia pantailan (x koordenatua)</longdesc>
                                        </local_schema>
                                </entry>
                                <entry name="window_height">
                                        <local_schema short_desc="Leihoaren altuera">
                                                <longdesc>Leihoaren altuera lehenetsia (pixeletan)</longdesc>
                                        </local_schema>
                                </entry>
                                <entry name="window_width">
                                        <local_schema short_desc="Leihoaren zabalera">
                                                <longdesc>Leihoaren zabalera lehenetsia (pixeletan)</longdesc>
                                        </local_schema>
                                </entry>
                                <entry name="clear_entry">
                                        <local_schema short_desc="Garbitu sarrera bilaketako emaitza hautatu ondoren">
                                                <longdesc>Gaitzen bada sarrera garbituko du bilaketako emaitza hautatu ondoren</longdesc>
                                        </local_schema>
                                </entry>
                                <entry name="collapsed_cat">
                                        <local_schema short_desc="Tolestutako kategoriak">
                                                <longdesc>Kategorien zerrenda bistaratzean tolestatzeko. Baliozko kategoriak: lehenetsia, historia, dokumentuak, posta, berriketak, fitxategiak, pertsonak, lekuak, ekintzak, web guneak, web bilaketak, berriak eta oharrak.</longdesc>
                                        </local_schema>
                                </entry>
                                <entry name="enabled_handlers">
                                        <local_schema short_desc="Gaitu kudeatzaileak">
                                                <longdesc>Gaitutako kudeatzaileen esportatutako klase-izenen zerrenda lehentasunaren arabera ordenatutz. Ezkerrenen dagoenak lehentasun handiagoa du.</longdesc>
                                        </local_schema>
                                </entry>
                                <entry name="keybinding">
                                        <local_schema short_desc="Laster-teklak">
                                                <longdesc>Tekla-sekuentziak deskbar-appletean fokua jarriko du, azkar idaztea eskainiz</longdesc>
                                        </local_schema>
                                </entry>
                                <entry name="use_selection">
                                        <local_schema short_desc="Deskbar-appleta abiaraztean uneko hautapena itsatsiko den edo ez">
                                                <longdesc>Aukeratu laste-teklak uneko hautapena itsatsiko duen edo ez bilaketako koadroan.</longdesc>
                                        </local_schema>
                                </entry>
                                <entry name="typingdelay">
                                        <local_schema short_desc="Bilaketa hasi aurretik igaroko diren milisegundoak">
                                                <longdesc>Denbora (milisegundotan) bilaketako sarreran tekla sakatu eta uneko bilaketa hasieraren artekoa</longdesc>
                                        </local_schema>
                                </entry>
                                <entry name="minchars">
                                        <local_schema short_desc="Behar den gutxiengo karaktere-kopurua bilaketa hasteko">
                                                <longdesc>Idatzi beharreko gutxiengo karaktere-kopurua applet-ak bat datozenak erakusten hasteko</longdesc>
                                        </local_schema>
                                </entry>
                                <dir name="mozilla">
                                        <entry name="show_only_primary_search">
                                                <local_schema>
                                                        <longdesc>Hobetsitako bilaketako motorra soilik edo motor guztiak erakutsi. Honek Mozilla-n oinarritutako web arakatzaileei soilik eragiten die: adib. firefox.</longdesc>
                                                </local_schema>
                                        </entry>
                                </dir>
                        </dir>
                        <dir name="gweather">
                                <dir name="prefs">
                                        <entry name="coordinates">
                                                <local_schema>
                                                </local_schema>
                                        </entry>
                                        <entry name="location4">
                                                <local_schema>
                                                </local_schema>
                                        </entry>
                                        <entry name="location3">
                                                <local_schema>
                                                </local_schema>
                                        </entry>
                                        <entry name="location2">
                                                <local_schema>
                                                </local_schema>
                                        </entry>
                                        <entry name="location1">
                                                <local_schema>
                                                </local_schema>
                                        </entry>
                                        <entry name="location0">
                                                <local_schema>
                                                </local_schema>
                                        </entry>
                                </dir>
                        </dir>
                        <dir name="clock_applet">
                                <dir name="prefs">
                                        <entry name="format">
                                                <local_schema>
                                                </local_schema>
                                        </entry>
                                </dir>
                        </dir>
                </dir>
        </dir>
</gconf>[/SIZE]

---

### Post by jannen on 2008-09-26
Continuing from above message.... I run the **sudo dpkg --configure -a**
message again. This time I got different reply, it says

[B]dpkg: error processing compiz-fusion-plugins-main (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 compiz-fusion-plugins-main[/B]

Please advice... how can I fix this?
Many thanks.

---

### Post by Elfy on 2008-09-26
Try ```
sudo apt-get install -f
``` Please whole of any error message

---

### Post by jannen on 2008-09-26
Hi. Here it is:

[B]janne@Burrito:~$ sudo apt-get install -f
[sudo] password for janne: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. [/B]

Again running the:

janne@Burrito:~$ sudo dpkg --configure -a
dpkg: error processing compiz-fusion-plugins-main (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 compiz-fusion-plugins-main

---

### Post by jannen on 2008-09-27
Wish I knew more about this stuff... 

Any suggestion how to porceed? Ubuntu doesnt now allow to run the dpkg --configure -a... its in read only state. 

Help... !

---

### Post by jannen on 2008-09-28
I tried it again today the dpkg --configure -a

Now the issue is the following:
[B]
janne@Burrito:~$ sudo dpkg --configure -a
dpkg: unable to access dpkg status area: Read-only file system
[/B]

How can I proceed now, please advice! Im stuck with the whole issue, cant do any updates or installations!

Thanks (getting desperate!):confused:

---

### Post by Elfy on 2008-09-28
I've talked on the beg team channel - suggestion is to run fsck on your drive

[http://ubuntuforums.org/showthread.php?t=422307](http://ubuntuforums.org/showthread.php?t=422307) should help

I'm a bit confused/concerned that the error appears to change each time you run the command.

---

### Post by bobpaul on 2008-10-20
I'm in a very similar state. I'm running Intrepid beta and hadn't updated in a couple of weeks. After running them today I've seen the same general error, but for a number of default gconf xml files. Attached is the output of "apt-get install -f". Now metacity returns a segfault when it runs... not sure if that's related.

Edit: Installed xfce4 and am using that instead of gnome for the time being.

---

### Post by bobpaul on 2008-10-21
Not sure if the gconf2 or gconf2-common packages installs the xml files, but the following worked:

```
sudo apt-get purge gconf2 gconf2-common
sudo apt-get install -f
sudo apg-get install ubuntu-desktop
```

Please note that when you do the purge that ubuntu will remove a LOT of packages, including some applications you installed after installing ubuntu. When you reinstall ubuntu-desktop you will get back things like gnome and firefox, but not anything you installed after the fact that needed gconf2. It's a good idea to make note of the packages that are removed in the purge step. 'remove' *might* work instead of purge, but since 'aptitude reinstall' didn't work for me, I didn't bother trying it.

---

