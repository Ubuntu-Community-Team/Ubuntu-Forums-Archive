---
title: "how to suppress packages from upgrading ?"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by masuch on 2012-12-11
Hi,

I have a lot of packages compiled by myself in Ubuntu instance. Within each upgrade/distribution upgrade there is possibility those my compiled packages (libraries) are overwritten.

I would like to know some suggestions how to suppress to install and/or upgrade some specific packages ?

URLs, tips and tricks are welcomed. No gui software, only in terminal.

thank you very much for help,
kind regards,
M.

---

### Post by kleenex on 2012-12-11
Hi **masuch**. What about holding packages? Hold means that even if a newer version of that package is available it will not be upgraded. Example of holdind e.g. mysql

```
[COLOR=Blue]*# hold package*[/COLOR]
echo "mysql hold" | dpkg --set-selections

[COLOR=Blue]*# install package (unhold)*[/COLOR]
echo "mysql install" | dpkg --set-selections

# [COLOR=Blue]*check*[/COLOR] [COLOR=Blue]*the results:*[/COLOR]
dpkg --get-selections | grep mysql                        
mysql                                            hold
```Now, mysql (and dependencies) are being held back. I think that there are several methods of suppress to install and/or upgrade some specific packages.

---

### Post by masuch on 2012-12-11
> **kleenex said:**
> Hi **masuch**. What about holding packages? Hold means that even if a newer version of that package is available it will not be upgraded. Example of holdind e.g. mysql

```
[COLOR=Blue]*# hold package*[/COLOR]
echo "mysql hold" | dpkg --set-selections

[COLOR=Blue]*# install package (unhold)*[/COLOR]
echo "mysql install" | dpkg --set-selections

# [COLOR=Blue]*check*[/COLOR] [COLOR=Blue]*the results:*[/COLOR]
dpkg --get-selections | grep mysql                        
mysql                                            hold
```Now, mysql (and dependencies) are being held back. I think that there are several methods of suppress to install and/or upgrade some specific packages.


thank you, 

I know it was not within this question on the first place but I would like to ask anyway:

How to solve it within this case:
if the package was not installed - to hold the package does not work. 
What I am up is - when I compiled software by myself and I am going to install new (not installed) package/s - my compiled/installed software is going to be overwritten. How can I prevent to overwrite anything what I have compiled/installed by me ?

Is there any way how to cope with this ?
I can create script, but at this moment I am collecting information and getting mechanism how it works.

I just want my compiled and installed stuff - not to touch / change by installing new packages / upgrading existing packages.

I have been thinking about combination of
echo "package hold" | sudo dpkg --set-selections
and
dpkg-divert --add --rename --divert /usr/bin/command.real /usr/bin/command
but it is quite complicated.

If there is any way how to check the currently installed version against version is going to be installed - I would like to have it in the script as well.


thank you for any info.

---

### Post by kleenex on 2012-12-11
> (...) How can I prevent to overwrite anything what I have compiled/installed by me ? (...)
(...) If there is any way how to check the currently installed version against version is going to be installed (...) Hi **masuch**. So, I still think, that best method will be 'hold' your package before any system, packages updates. Another way _could be_ a process called - "pinning" packages (more info about pin can be found here ==>> [COLOR=Blue][AptPreferences]("http://wiki.debian.org/AptPreferences#A.2BAC8-etc.2BAC8-apt.2BAC8-preferences")[/COLOR]). An example of entry in  [COLOR=SeaGreen]/etc/apt/preferences[/COLOR] file  to "pin" the older versions and packages related with your program;
```
[COLOR=Purple]Package:[/COLOR] your_program
[COLOR=Navy]Pin:[/COLOR] version 1.0*
[COLOR=DarkSlateBlue]Pin-Priority:[/COLOR] 1001
``` 1001 entry sets the value for all [COLOR=SeaGreen]your_program[/COLOR] versions begin with [COLOR=Blue]1.0[/COLOR], regardless of the repository. A newer version (for example, starting with [COLOR=Blue]1.1[/COLOR]) is not installed, even if it is available, unless it would set an even higher priority.  More info about APT-Pinning: [COLOR=RoyalBlue]*[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)* 

[/COLOR][COLOR=RoyalBlue][COLOR=Black]So, how APT utility interprets the value of Pin-Priority? Let see:
[/COLOR]```
**[COLOR=Blue]P < 0[/COLOR]** : [COLOR=Black]Version of the package will not be installed.[/COLOR]
**[COLOR=Purple]0 < P < 100[/COLOR]** : [COLOR=Gray]Version of the package will be installed only if the package is not currently installed.[/COLOR]
**[COLOR=Teal]100 <= P < 500[/COLOR]** **:** [COLOR=Black]Version of the package will be installed, unless the version is available from another repository.[/COLOR]
[COLOR=DimGray]**500 <= P < 990** **:**[/COLOR] [COLOR=DimGray][COLOR=Gray]Version  of the package will be installed, unless there is a version derived from the repository designated as the "target release" or actually installed a newer version of the package[/COLOR].[/COLOR]
**[COLOR=Sienna]990 <= P <= 1000[/COLOR]** **:**[COLOR=Black] Version of the package will be installed even if you have a version derived from the repository designated as the "target release" unless you install a newer version of the package.[/COLOR]
**[COLOR=DarkOliveGreen]P > 1000[/COLOR]** : [COLOR=Gray]Version of the package will be installed, even if it requires its withdrawal[/COLOR]
```[/COLOR] To check which version of packages is currently installed you can use e.g.
```
[COLOR=Red]$[/COLOR] [COLOR=SeaGreen]dpkg -s firefox |grep Version[/COLOR]
Version: 17.0.1
``` For more detailed output, use this [COLOR=Blue]dpkg [/COLOR]command without [COLOR=SeaGreen]grep Version[/COLOR]. To check which packages will be installed, you can simulate the update process. APT utility, allows such option and it is very interesting, because you do not have to install available updates, but only check what, eventually, could be installed.
```
[COLOR=Blue]*#*[/COLOR][COLOR=Blue]* simulating an update process;*[/COLOR]
[COLOR=Red]$[/COLOR] sudo apt-get -s upgrade
```  One more thing. You have written, that "*if the package was not installed - to hold the package does not work*". This seems to be a logical, right? 

Cheers!

---

### Post by masuch on 2012-12-15
Hi, thanks a lot for "pinning" hint. It solved many of my concerns. Going to mark this thread as solved.

I am not clear about one thing:

Concerning the "not-installed packages" I had in mind:
- How do I test ?
If software has been compiled/installed by me - not using package/s (software was not installed previously or has been purged) and suddenly within apt-get upgrade process (it could be even dependent libraries) it appeared to try to install software/package/s which are going to rewrite my installed program (because software were not installed previously using deb package/s how can I use any principle previously mentioned to compare installed software version with on ongoing installation process ?).

If you already described it - Please accept my apology, I did not get it.

---

### Post by kleenex on 2012-12-18
Hi, **masuch**. Really do not know. I think that's all. I mean that I was able to help you. Sorry.

---

