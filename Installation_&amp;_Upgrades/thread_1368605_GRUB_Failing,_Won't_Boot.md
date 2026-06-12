---
title: "GRUB Failing, Won't Boot"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by gonzogonzo on 2009-12-30
Hello there everyone.

I am attempting to install 9.10 ubuntu onto an old HP with 3.20 Ghz and a gig of RAM. It has two physical hard drives in it, one an 80 gig and the other a 30. I have been trying to do a full install on the 80, and there is currently no other operating system on the computer.

Installing goes fine, I choose erase and install on the whole disc, until I restart and a cursor just blinks on a blank screen. No OS comes up. Researching the problem, I figured it was a GRUB issue with the MBR and attempted a variety of fixes, including booting into a live cd and using the terminal to attempt to reroute grub to the proper root partition and hope that made the MBR load Grub. The terminal always tells me GRUB does not exist and when I try and install it I just get more error messages. I've tried apt-get update, apt-get grub-install, and even mounting my root partition and trying to access GRUB from there after chrooting the livecd profile onto the root partition. I can't find GRUB, nothing will work and three days of this is taking a toll on me. Where am I going wrong in the installation? Both hard drives are completely empty, why won't Ubuntu load after installation?

Somebody please help me, I need my computer back.

---

### Post by Bucky Ball on 2009-12-30
Install 8.04 LTS and give 9.10 another six months. 8.04 is the current long term support, enterprise release, rock solid and lots of support and probably a good place to start. There are so many problems with 9.10 right now.

---

### Post by gonzogonzo on 2009-12-30
I will give that a try, I have gotten earlier versions of ubuntu to work without a hitch before.

---

### Post by Sef on 2009-12-30
> The terminal always tells me GRUB does not exist and when I try and install it I just get more error messages.

What do the error messages say exactly?

---

### Post by presence1960 on 2009-12-30
Let's see exactly what is on your machine there. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Without this info we have a better chance of finding a needle in a hay stack because we will be probing blindly at what MAY be the problem.

---

### Post by gonzogonzo on 2009-12-31
> **presence1960 said:**
> Let's see exactly what is on your machine there. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Without this info we have a better chance of finding a needle in a hay stack because we will be probing blindly at what MAY be the problem.
Alright, I tried to go back with the LTS version and it wouldn't even boot from my USB. Over the last few days I have also narrowed down that my DVD drive may be having some optical problems and not reading ISOs, so I am doing all of this from a Live USB environment.

In 9.10 I open the terminal and type the sudo bash command, and it just says something to the effect of ubuntu /desktop/boot file already exists, it doesn't give me a TXT file to my desktop. I know the MBR is shot because it never loads grub, but when I reinstall, why won't Ubuntu write it's own MBR? Both hard discs are empty (other than the full installation of Ubuntu that is on there now) when I install!

Thank you everyone for the help. I am normally pretty competent with a computer so this is kind of upsetting.

---

### Post by presence1960 on 2009-12-31
> **gonzogonzo said:**
> Alright, I tried to go back with the LTS version and it wouldn't even boot from my USB. Over the last few days I have also narrowed down that my DVD drive may be having some optical problems and not reading ISOs, so I am doing all of this from a Live USB environment.

In 9.10 I open the terminal and type the sudo bash command, and it just says something to the effect of ubuntu /desktop/boot file already exists, it doesn't give me a TXT file to my desktop. I know the MBR is shot because it never loads grub, but when I reinstall, why won't Ubuntu write it's own MBR? Both hard discs are empty (other than the full installation of Ubuntu that is on there now) when I install!

Thank you everyone for the help. I am normally pretty competent with a computer so this is kind of upsetting.
You are doing somrthing wrong then. Either you haven't downloaded the file to desktop or you are typing the command incorrectly. Here are the steps in order you need to do.
1. Boot Live CD and go to desktop.
2. Come back here.
3. click on _Boot Info Script_ in my signature line. This will download the the file.
4. Make sure the downloaded file is on your desktop. If it is not then move it there.
5. Open a terminal and copy/paste the command from here to terminal. 

```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

