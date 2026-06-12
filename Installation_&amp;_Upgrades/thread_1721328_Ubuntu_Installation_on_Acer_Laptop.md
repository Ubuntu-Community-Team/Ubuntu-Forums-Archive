---
title: "Ubuntu Installation on Acer Laptop"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by dontbugmee on 2011-04-04
Hi,
Recently, i had trouble installing XP in my Acer laptop. But then sorted it out changing SATA settings to IDE.

Initially i had problem installing ubuntu 9, the laptop provider said that 9.10 ubuntu is incompatible to your latest laptop, you need to have latest version of ubuntu. I dont know the reason why OLD Version of ubuntu dont work in my new laptop.So,  I've tried installing Ubuntu several times, but there an error that bugs me everytime.
I've attached the images of the related problem. It says faulty harddisk/DVD, but i've downloaded a new copy of ubuntu into a new CD, yet its not working. I have tried installing wubi in the same partion of WindowsXP.

Can anyone solve this problem? [Please Check the Images]

---

### Post by dontbugmee on 2011-04-04
Few more Images. The error that continued are shown in successive images.

---

### Post by oldfred on 2011-04-04
I do not know much about wubi.

Another thread discussing similar issues.
[http://ubuntuforums.org/showthread.php?t=1720946](http://ubuntuforums.org/showthread.php?t=1720946)

---

### Post by dontbugmee on 2011-04-04
hi, But the problem from the other thread seems to be different. My system is 64bit.
The problem is clearly described in the image.

I hope someone who faced this before answers.

---

### Post by dontbugmee on 2011-04-05
Anyone with answer?

---

### Post by deconstrained on 2011-04-05
> **dontbugmee said:**
> I dont know the reason why OLD Version of ubuntu dont work in my new laptop.

Same reason why any old version of *[color=gray][operating system][/color]* isn't guaranteed work with newer *[color=gray][hardware item][/color]*; thing changed since that distribution of *[color=gray][operating system][/color]* was released, so it's not guaranteed to support *[color=gray][hardware item][/color]*, especially if *[color=gray][hardware item][/color]* entered the market after the said version of *[color=gray][operating system][/color]* was released (unless the organization/company that maintains it released patches and bugfixes for *[color=gray][hardware item][/color]*). This is especially true of GNU/Linux distributions; they change really fast, adding new auto-config scripts and configurations and modules to accomodate new hardware all the time, so what doesn't work in 2009 may be fixed by 2010 (but it doesn't often work the other way around).

Long story short, grab a torrent file and download a newer ISO.

---

### Post by bcbc on 2011-04-05
Run chkdsk /r (My computer, right click on drive, Properties, Tools, Check disk for errors, fix automatically, reboot to complete).
Defragment the drive as well

Try again. If it still fails, boot from an Ubuntu CD in live CD mode (try without installing) and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

---

### Post by dontbugmee on 2011-04-05
@ , 
ran chkdsk, and also defragmented the disk... but the problem persists...
It says to report at [https://launchpad.net/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/ubuntu/+source/ubiquity/+filebug)
ang it precedes me to attach logs
" var/log/partman
var/log/sys*** "

Dont remember the log name exactly, but when i boot from windows to check in log location, there is no such folder location.

---

### Post by bcbc on 2011-04-05
> **dontbugmee said:**
> @ , 
ran chkdsk, and also defragmented the disk... but the problem persists...
It says to report at [https://launchpad.net/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/ubuntu/+source/ubiquity/+filebug)
ang it precedes me to attach logs
" var/log/partman
var/log/sys*** "

Dont remember the log name exactly, but when i boot from windows to check in log location, there is no such folder location.
It's a little involved to do this on wubi. When you get the message "Completing the installation... Press ESC for more options" you have to hit ESC, then select the Verbose option. Then when you get that failure, you have to drop to a shell (CTRL+ALT+F2) and run: "sudo sh /custom-installation/hooks/failure-command.sh". It basically zips the logs into C:\ubuntu\installation-logs.zip

See this for more info: [https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide#Wubi%20Support%20Forum")

I saw someone post that you should use a dummy password when you do this as it may be included in one of the logs.

---

### Post by dontbugmee on 2011-04-05
hi bcbc, before i try verbose installation. i boot ubuntu using CD (LiveCD), and then ran  [bootinfoscript]("http://bootinfoscript.sourceforge.net/") using terminal. using command ' chmod +x location/bootinfoscrop.sh. There was no output after i ran that script. Is that Okay?

I need to now try verbose mode installation now and will then come back.
OMG, Acer troubles a lot! I've never experienced this complications in any comp.

---

### Post by dontbugmee on 2011-04-05
Tried verbose mode, the command sh seems like not working in my computer... Some people said that Acer Laptop is not a good buy, i made a mistake buying it, and customer support is also not good.

So many problems

---

### Post by bcbc on 2011-04-05
> **dontbugmee said:**
> hi bcbc, before i try verbose installation. i boot ubuntu using CD (LiveCD), and then ran  [bootinfoscript]("http://bootinfoscript.sourceforge.net/") using terminal. using command ' chmod +x location/bootinfoscrop.sh. There was no output after i ran that script. Is that Okay?

I need to now try verbose mode installation now and will then come back.
OMG, Acer troubles a lot! I've never experienced this complications in any comp.
chmod +x just marks it as executable. This is not necessary. You need to run it as described in that link. e.g. usually it downloads to my ~/Downloads directory.

So you need to then go to a terminal (CTRL+ALT+t) and then:
```
cd Downloads
sudo bash boot_info_script055.sh
[enter password]
```

Then after that there'll be a RESULT.txt file you can open, and copy and paste the results here between [CODE[SIZE=1] [/SIZE]][/CODE] tags.

---

### Post by bcbc on 2011-04-05
> **dontbugmee said:**
> Tried verbose mode, the command sh seems like not working in my computer... Some people said that Acer Laptop is not a good buy, i made a mistake buying it, and customer support is also not good.

So many problems
I think there might a problem with that script. You can zip the logs manually:
```
sudo zip -r /host/ubuntu/installation-logs.zip /var/log
```

---

### Post by dontbugmee on 2011-04-05
Why somuch problems installing ubuntu?
I dont know, feels like forget installing Ubuntu.
Why Acer Manufacturers keep everything so cryptic?

---

### Post by bcbc on 2011-04-05
> **dontbugmee said:**
> Why somuch problems installing ubuntu?
I dont know, feels like forget installing Ubuntu.
Why Acer Manufacturers keep everything so cryptic?

I wouldn't say there are so many problems. When it works - it's a breeze. When it doesn't work you need to find the cause and fix it.

How about that bootinfoscript result?

---

### Post by dontbugmee on 2011-04-10
I'm gonna try install any other version of ubuntu...
if that wont work, i'm gonna stop trying.

---

### Post by dontbugmee on 2011-04-11
The error was due to 'md5 error due to the disk'. There are some apps like 'MD5 Check' to check whether downloaded iso file is proper. I sorted it out.

---

