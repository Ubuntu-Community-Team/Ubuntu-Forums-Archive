---
title: "freezes on 2nd reboot,"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by itk on 2013-03-06
1. i installed with wubi from windows xp on my "H:" drive wich has 522GB free and restarted [snapshot]("https://docs.google.com/file/d/0B8aocZf_K51ROGtvMWpiVEtGcHc/edit?usp=sharing")
2. i chose ubuntu from the boot loader and it started installing [snapshot]("https://docs.google.com/file/d/0B8aocZf_K51RV045anJueXJHWkU/edit?usp=sharing")
3. after it restarted, i chose ubuntu in the normal boot loader, and again in the 2nd boot loader [grub?] and then it froze [snapshot]("https://docs.google.com/file/d/0B8aocZf_K51RRHRIZVJIYmkyaVE/edit?usp=sharing")
i tried all the shortcuts and nothing
keyboard seems to be working fine since i can turn on\off num&caps lock, i pressed [ctl][alt][del]
4. tried the advanced options, 1st choice, froze again [snapshot]("https://docs.google.com/file/d/0B8aocZf_K51RSEhBQ3ZzeWRvbnc/edit?usp=sharing")
5. tried the advanced options, 2nd choice, this time i got this: [snapshot]("https://lh4.googleusercontent.com/G5PkyXKK7_gp2B5h_ylVQXkSA-ylbIClhmaz0S2SOhm8pmZhUxjePsdUy8zv8VR9qg=w1600")

i don't know anything about linux and i really want to try, if anyone can help me solve this problem!

> For installation  logs see /var/log/syslog and /var/log/installer within Linux and  C:\ubuntu\installation-logs.zip within Windows. If you do not have  C:\ubuntu\installation-logs.zip, uninstall, reinstall, select "Verbose  Mode" at boot (see above). When the installer stops press CTRL+ALT+F2  and run: "sudo sh /custom-installation/hooks/failure-command.sh". You  can now reboot into Windows, the logs should be in  C:\ubuntu\installation-logs.zip
Post installation logs are in /tmp and /var/log/syslog 


Windows side installation logs: [wubi-12.10-rev273.log]("https://docs.google.com/file/d/0B8aocZf_K51RNF9qeUUxZ1d2bTQ/edit")
/var/log/installer/[casper.log]("https://docs.google.com/file/d/0B8aocZf_K51RTGt1TExmSzBTMWs/edit?usp=sharing") [DiskInternals Linux Reader]
/var/log/syslog <empty>

windows xp professional sp3
cpu: intel q6600
ram: 4gb
gpu: nvidia gt8600
motherboard: asus p5qd turbo
hdd: 5 ide hard drives

---

### Post by bcbc on 2013-03-07
For your graphics card you require nomodeset:

[http://askubuntu.com/a/257917/14916](http://askubuntu.com/a/257917/14916)

---

### Post by itk on 2013-03-07
thanks for the reply!
i followed the instructions
and it still freezes in the second boot 

i uninstalled and reinstalled:
in the first boot i pressed ESC, edited "Normal" and added nomodeset then [ctl]+[x]
in the second boot i edited the first entry "ubuntu", added nomodeset then [ctl]+[x] [screenshot ]("https://docs.google.com/file/d/0B8aocZf_K51RRE41b0FDUmxHMjA/edit?usp=sharing")
same thing, it freezes :/

any other things i can try?

---

### Post by bcbc on 2013-03-07
Just confirm - that's a cursor following nomodeset right? You didn't add nomodeset_ ?

I'm assuming everything was correct.

You could try noacpi as well as nomodeset. Also someone with a similar model was having issues with power management enabled: [http://askubuntu.com/q/50833/14916](http://askubuntu.com/q/50833/14916)

Finally, I'd check if there are any BIOS updates available.

PS if noacpi works, then you should still try other options, because that can disable many useful features.

---

### Post by itk on 2013-03-07
> **bcbc said:**
> Just confirm - that's a cursor following nomodeset right? 
yes

tried [noacpi with nomodeset]("https://lh4.googleusercontent.com/4Xg0ri0lzAOR8WcubS-0cjeJb5Rri7JwAsKuIElm0uJS6iyDJGcjB2repRrksbKH6w=w1600") its the same
also tried to disable power management, no difference, except xp didn't boot so i enabled it.

i checked the bios, they are up to date, i have the latest version.

:/

---

### Post by bcbc on 2013-03-07
Doesn't look good.

Maybe try 12.04? Or try booting one a live CD of lubuntu/xubuntu and see if that works better.

---

