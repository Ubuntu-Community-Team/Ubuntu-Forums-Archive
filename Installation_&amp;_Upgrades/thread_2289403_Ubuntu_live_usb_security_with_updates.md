---
title: "Ubuntu live usb security with updates"
date: 2015-08-03
forum: Installation &amp; Upgrades
---

### Post by G_Blackburn on 2015-08-03
I use Ubuntu without installing by running from a live usb stick.  I recently updated from 14.04.1 to 14.04.2 but have not noticed much difference.

Are their any security benefits from upgrading if using live usb without installing linux.  I use for web browsing, banking etc so would like to stay secure via linux but don't really want to use my limited bandwidth updating if there are no additional security benefits.

Would I be safe not updating at all.  Maybe every 5 years?  Did the update give me any added security benefits?

---

### Post by grahammechanical on 2015-08-03
Perhaps you should become a regular reader of Ubuntu Weekly Newsletter. There is a link to it on this forum. Always there is a section called Updates & Security for 12.04, 14.04 and 15.04. It is a list of the latest vulnerabilities.

Only you can take responsibility for your practice of keeping your installation up to date. Or not, as the case may be.

Regards

---

### Post by ubfan1 on 2015-08-04
Kernel updates are not possible with the live media, but application updates, like your browser, will certainly work.

---

### Post by G_Blackburn on 2015-08-04
Good to know I can update the browser.  Would anyone know if the persistents can be changed.  I'd like to update the browser then set so no space left for updates so the image always boots without changes.  Then when necessary expand the space again to allow updates of the browser.  I know this can be done on hard drive partitions so hoping possible on memory card?

---

### Post by sudodus on 2015-08-04
See the sticky threads in the [Ubuntu Security subforum](http://ubuntuforums.org/forumdisplay.php?f=338)

See also this link: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

-o-

I think there will be problems if you tamper with the size of the casper-rw file or partition like you describe. Download/Upgrade the current iso file of a rolling release (or use the Ubuntu developing version, now Wily Werewolf to become 15.10), if you want high security with a live system. I think such a live system without persistence is safer than a persistent live system.

---

### Post by C.S.Cameron on 2015-08-04
I have found that once persistence gets filled the drive will not boot.
Persistence is turned on by the word persistent located in the file txt.cfg in a Startup disc creator build, syslinux.cfg in a UNetbootin build and grub.cfg in a grub2 build.

---

### Post by G_Blackburn on 2015-08-04
O.K Thanks.

I tried messing with the size of casper-rw and crashes on boot just as stated. :)

So please clarify the following as i'm not the brightest of people.

Question 1. 
Security is better with a none changing live usb stick (no persistence) than using one with persistence and ability to update browser?  I thought with persistence just as secure seeing as caught viruses through browser cant effect linux?

[COLOR=#333333][FONT=Ubuntu]Question 2.
Ubuntu 15.04 and 14.04.2 LTS are different linux OS and equally secure?  I assumed they were different as one without the LTS.  If not then I have wasted my bandwidth downloading the older 14.04.2 LTS. [/FONT][/COLOR]

---

### Post by sudodus on 2015-08-05
Malware will not survive reboot in a live system, so a fresh live system without persistence is rather safe.

I can't tell if either of Ubuntu 15.04 and 14.04.2 LTS is safer. Both receive security updates as soon as possible. The LTS release is better polished and debugged, but older.

But it is important to understand that there are many security holes, that are not directly related to the operating system. Did you read the links in post #5?

For example, your browsing habits are very important. If you reboot a live system without persistence, only perform the bank transactions, and shutdown or reboot again, this risk is reduced.

But many people use an up to date installed linux system without problems. I do since several years. You can have two linux systems installed. One system for general usage, and one system for banking.

Reboot into the banking system, run

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and (only) if there is a kernel upgrade, reboot again. Then you have an up to date installed system.

Do your banking transactions and nothing else.

Reboot into your system for general usage again.

---

### Post by G_Blackburn on 2015-08-05
Thanks for the replies and info.

I did have a read at link #5

I think I will stick with a none persistent yearly update of the LTSs version.  I think that will keep me safe as can be expected as long as i freshly reboot each time before banking etc.  Hopefully the yearly update will be enough to prevent the majority of loopholes.  I suspect that would be much safer than using Windows 7 with regular updates, maleware and virus scanners etc.

Am I correct in thinking no firewall is needed.  I did notice a few bytes of info on my bandwidth monitor even though the mozilla browser was closed.  I thought all ports were blocked on Linux as default so don't know why there would still be a few bytes of internet data showing on bmon?

Thanks for the info about the sudo update options.  I will add those commands to my notes.  I never knew about that.  May therefore be worth using a version with persistence on and making sure I only use for shopping payments and banking. :)

---

### Post by sudodus on 2015-08-06
Things are safer if your computer is 'behind' a router. Most routers have a simple firewall.

I don't know much about firewalls, so let us wait for a reply from someone who knows more than I about it.

---

