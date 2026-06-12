---
title: "Installing WASCE(Websphere Application Server Community Edition) on ubuntu"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by ayazpasha2434 on 2008-09-15
Hi All,

I am just following this link [http://publib.boulder.ibm.com/wasce/V1.1.0/en/Tasks/Install/Installing.html]("http://publib.boulder.ibm.com/wasce/V1.1.0/en/Tasks/Install/Installing.html") in order to install WASCE(Websphere Application Server Community Edition) on UBUNTU.

I am not able to find the wasce_ibm150sdk_setup-version-ia32linux.tar file which is the starting step for installation.

Please help:(

---

### Post by Partyboi2 on 2008-09-15
It looks like you need to register before you can download the file. You can do that [[COLOR=Blue]here[/COLOR]]("https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?source=wsced")
[[COLOR=Blue]Here[/COLOR]]("http://bytesforbreakfast.blogspot.com/2008/01/ubuntu-specific-installation.html") is another good tutorial to use to install it

---

### Post by ayazpasha2434 on 2008-09-17
Thanks for reply Partyboi2,

I tried signing in and downloading the wasce_ibm150sdk_setup-2.1.0.1-ia32linux.tar.bz2 but I am not able to download it successfully, I am facing this exception>  Download Director applet cannot be loaded.
 Java support must be enabled to run.

 For help see Frequently Asked Questions

Please Help!!!

---

### Post by ayazpasha2434 on 2008-09-17
This problem is fixed, I just had to select the option 'Download using HTTP' rather than 'Download using Download Director'.> **ayazpasha2434 said:**
> Thanks for reply Partyboi2,

I tried signing in and downloading the wasce_ibm150sdk_setup-2.1.0.1-ia32linux.tar.bz2 but I am not able to download it successfully, I am facing this exception>  Download Director applet cannot be loaded.
 Java support must be enabled to run.

 For help see Frequently Asked Questions

Please Help!!!
 I will download the tar file and then start installing it, I will post queries if I come accross with any.

Thanks

---

### Post by Partyboi2 on 2008-09-17
All the best :)

---

### Post by ayazpasha2434 on 2008-09-17
I have now successfully downloaded the wasce_setup-2.1.0.1-unix.bin and started the server using ./startup.sh command, I want to know what tail command can I give to checkout the server log in command prompt.

Thanks

---

### Post by ayazpasha2434 on 2008-09-23
The tail command is tail -f ../var/log/server.out

I also want to know how I can install Liferay on WASCE. Please Help!!!

---

### Post by jesley8q on 2010-08-12
Aukcell is a seasoned and recognized expert in all aspects of Liferay deployment ,which is based in China. Our services including Architecture, Theme, Custom portlets, Migration from other portals…. and many more 

Please feel free to contact us :
 
24/7 Support: Skype : aukcell AIM: eonpeter
 
Email  [EMAIL="support@aukcell.com"]support@aukcell.com[/EMAIL]
[http://www.aukcell.com](http://www.aukcell.com)

---

