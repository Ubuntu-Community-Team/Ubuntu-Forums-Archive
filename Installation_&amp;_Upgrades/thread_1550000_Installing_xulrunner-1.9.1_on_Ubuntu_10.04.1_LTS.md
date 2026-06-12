---
title: "Installing xulrunner-1.9.1 on Ubuntu 10.04.1 LTS"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by Maciej Miklas on 2010-08-10
Hi,

I have 64 bit ubuntu with Eclipse Helios 64 bit. I am getting org.eclipse.swt.SWTError: XPCOM error -2147467259.

Currently my installation has xulrunner 1.9.2.3 and 1.9.2.8. I need 1.9.1 to solve my problem.

I have tried to install it, but it gives an error:
$ sudo apt-get install xulrunner-1.9.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xulrunner-1.9.1 is not available, but is referred to by another package.


How can I install xulrunner-1.9.1 on my ubuntu without destroying firefox ?

Thank you!

---

### Post by Frogs Hair on 2010-08-10
I did some searching and found that you _may_ need to install FF 3.5 to get Xulrunner 1.9.1

---

### Post by Maciej Miklas on 2010-08-10
there must be a way to install just this package...

anyway installing FF 3.5 is also hard. I've tried to select FF 3.5 in Synaptic Package Manager and it installs 3.6....  every version  links to FF 3.6.

I really need some more help here....

---

### Post by Maciej Miklas on 2010-08-10
OK - I have the firefox 3.5 running. it does not have xulrunner, it has libxpcom.so....

---

### Post by Maciej Miklas on 2010-08-11
First I need to find 64 bit firefox or xulrunner.

This is really hard - every page points to 32 bit. Does anyone know 64 bit download link?

---

### Post by wojox on 2010-08-11
Try checking with [lovinglinux]("http://lovinglinuxblog.blogspot.com/")

Real good with anything Firefox.

---

### Post by Maciej Miklas on 2010-08-11
I was hoping to ges atp-get command to install xulrunner or something like that :(

---

### Post by Maciej Miklas on 2010-08-19
anyway I've found the problem.

I have installed flash 32 bit and this has replaced xulrunner with 32 bit.... I just reinstalled xulrunner and firefox. Now it works. But still... I would like to know if ubuntu supports installing older versions of libs parallel with new one

---

### Post by alex.mobigo on 2010-08-22
hi Maciej Miklas,

I have the same problem and same need.
Could you tell us the steps you made to re-install xulrunner-1.91 and FF 3.5?

I wonder if you needed to downgrade FF to embed it in Eclipse. 
I am trying to run Eclipse ATF in Ubuntu 10.04 64-bit without success.

Thanks if you can help us.

Alex

---

### Post by Maciej Miklas on 2010-08-22
1) you can force eclipse to use other renderer - in this case there is not need to reinstall xulrunner:
[http://www.eclipse.org/swt/faq.php#browserwebkitgtk](http://www.eclipse.org/swt/faq.php#browserwebkitgtk)
./eclipse -vmargs -Dorg.eclipse.swt.browser.UseWebKitGTK=true

2) or use package manager, deinstall firefox and xulrunner - this will remove lot of packages. After that install it again - it will automatically get 64 bit version.

---

### Post by alex.mobigo on 2010-08-22
Thanks for the quick reply,

This is not a renderer issue only, it is also javascript debugging issue.
Do you have javascript debugging with webkit?

xulrunner-1.9.1 is from ubuntu 9.04 FF3.5 and i think it might break a lot of packages on 10.04.

I have an ubuntu 9.10 that i upgraded from 9.04 and it kept a copy of xulrunner-1.9.1, if webkit cannot handle javascript debugging inside eclipse i will try to point eclipse to use this old version if possible, before i break my ubuntu 10.04.

i will tell the results for those who need javascript debugging in eclipse ATF if not possible with webkit

thanks,

alex

---

### Post by Maciej Miklas on 2010-08-22
I am only server developer - never tried java script.

Anyway - I've tried pointing eclipse to another xlurunner - this is just not working.... I've also tried this test app that shows xulrunner that eclipse it taking - it semas that this -D property does not switch xulrunner - it's being read from global registry (same routine as firefox is using).

I've tried also parallel install of firefox 3.0 - well it contains some xulrunner libs, but not all.... so this did not work as well.

But I know some fornt-end developers, that are using clean ubuntu 10.x-64Bit installation and it works without any problems - they did not install 32 bit flash, and this is probably causing problems

---

### Post by alex.mobigo on 2010-08-22
Thank you again.

Yes, i have 32 bit flash installed. If this is the cause, i will do a fresh install.

I did install xulrunner-1.9.1.
I dont get XPCOM error any more, but i get Mozilla error while Eclipse tries to edit a debugging section. I guess i need firefox-3.5, so i installed it but ubuntu keeps finding firefox 3.6 to run.

Could you check with the guys which firefox version they are using and which xulrunner-1.9.2 is installed?

Thanks.

alex

---

### Post by Maciej Miklas on 2010-08-23
the are using the newest version with all updates.

And I've had the same problem actually.... after resistalling xulrunner elcispe was working, but it had a few problems.

i reinstalled ubuntu completly and not everything works fine.... this is not optimal - but as you can see I did not get any help to resolve it in other way ;)

---

