---
title: "Ubuntu or Kubuntu with two cd's"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by COKEDUDE on 2013-11-30
Is it possible to install Ubuntu or Kubuntu with 2 cd's? The live cd's are now bigger than a single cd can handle now. I don't have any dvd's where I am or a big flash drive where I am.

---

### Post by ibjsb4 on 2013-11-30
To answer your question, nope, you need to burn a DVD for 13.10.

I can think of two options

#1  You could run 12.04 (which fits on a single CD).  or ..

#2  You could use the mini iso (also fits on a single CD) to install 13.10.

---

### Post by COKEDUDE on 2013-11-30
> **ibjsb4 said:**
> To answer your question, nope, you need to burn a DVD for 13.10.

I can think of two options

#1  You could run 12.04 (which fits on a single CD).  or ..

#2  You could use the mini iso (also fits on a single CD) to install 13.10.

Where do I get the mini iso? I have never heard of that.

---

### Post by deadflowr on 2013-11-30
[Here's the mini]("https://help.ubuntu.com/community/Installation/MinimalCD")

Select which version you want.

You'll need a working internet connection.

---

### Post by COKEDUDE on 2013-11-30
> **deadflowr said:**
> [Here's the mini]("https://help.ubuntu.com/community/Installation/MinimalCD")

Select which version you want.

You'll need a working internet connection.

Whats the difference between 64-bit PC (amd64, x86_64), 64-bit PowerPC**, and Itanium (IA-64)**?

---

### Post by ibjsb4 on 2013-11-30
You should have a 64bit processor and that would use the 64bit PC (amd64, x86_64) download.

What kind of computer do you have?  How much ram?  If this is a older computer, you may not be able to run Ubuntu.

And you need a [COLOR=#ff0000]wired[/COLOR] internet connection to use the mini iso.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mini+iso&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mini+iso&sa=Search&cof=FORID:9)

---

### Post by COKEDUDE on 2013-11-30
> **ibjsb4 said:**
> You should have a 64bit processor and that would use the 64bit PC (amd64, x86_64) download.

What kind of computer do you have?  How much ram?  If this is a older computer, you may not be able to run Ubuntu.

And you need a [COLOR=#ff0000]wired[/COLOR] internet connection to use the mini iso.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mini+iso&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mini+iso&sa=Search&cof=FORID:9)

Its a brand new Toshiba Satellite laptop. It has 8 GB of ram. 

I'm having a lot of trouble with the UEFI and secure boot. I haven't been able to find any good documentation on how to deal with UEFI and secure boot. I have switched from UEFI to csm and disabled secure boot, but that hasn't worked.

---

### Post by ibjsb4 on 2013-12-01
> I'm having a lot of trouble with the UEFI and secure boot. I haven't been able to find any good documentation on how to deal with UEFI and secure boot. I have switched from UEFI to csm and disabled secure boot, but that hasn't worked. 


Note: While the mini ISO is handy, it isn't useful for installing on UEFI-based systems that you want to run in UEFI mode. The mini lacks the proper files for booting the computer in UEFI mode. Thus, the computer will boot in BIOS compatibility mode, and the installation will be in BIOS mode. For more information, please see this. 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi&sa=Search&cof=FORID:9)

If this is still an issue, maybe you should start a thread on it.

---

