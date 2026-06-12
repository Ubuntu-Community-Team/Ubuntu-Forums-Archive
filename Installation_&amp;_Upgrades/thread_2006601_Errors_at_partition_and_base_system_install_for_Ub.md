---
title: "Errors at partition and base system install for Ubuntu and Kubuntu"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by amityweb on 2012-06-19
I am trying to install Ubuntu Server. I also tried Kubuntu. 

Previously Ubuntu was on the system and I think it worked OK, but it was an older version and I had upgrade errors, so I decided to do a fresh install. 

Both failed to either partition or install the system. Sometimes it would fail at partition stage with some input/output error, then the furthest I got was with Ubuntu, it had an error installing the base system. 

So I thought the hard drive had an issue. I bought a new hard drive. But its the same problem. 

I run a scan/test of the hard drive AND memory from the Ubuntu install screen and they state it is OK. 

Does anyone know what other problems I could have? e.g could the motherboard have an issue? I have no idea what to look for next. 

Thanks

---

### Post by sudodus on 2012-06-19
Welcome to the Ubuntu Forums :-)

It will be easier if you tell us more  about the computer: cpu, ram and graphics card or chip

What version of Ubuntu were you using earlier?

Are you trying to install the server with or without a graphic desktop environment?

How do you try to install it? From the mini iso or from the alternate iso? Have you tried to run a live session booted from one of the standard [KLX]ubuntu CD or USB drives?

Maybe you need to use some boot option. See this link
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

### Post by oldos2er on 2012-06-19
> **amityweb said:**
> I run a scan/test of the hard drive AND memory from the Ubuntu install screen and they state it is OK. 


Did you test the integrity of the *.iso files you downloaded? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you created a LiveCD, it should have 'Check disc for defects' when the first menu comes up.

---

### Post by amityweb on 2012-06-20
I checked the Ubuntu CD Rom integrity using the CD and said it was OK. 

I decided to install Windows, which installed absolutely fine, then use a partition manager to setup the ext3 and swap partitions. 

I then ran the Ubuntu install and this time it got further than before. It got as far as asking me if I want to setup a proxy, it then was installing the base system, but then it stopped saying An Installation Step Failed, but did not say what step or give an error. Not vey helpful is it!

So seems Windows works fine, I dont think there is an issue with the computer. I have had it for a couple of years, I cant remember what the make up of it is, but it has run Ubuntu and Windows 7 fine in the past. Only now I want to reinstall it, Ubuntu and Kubuntu wont work. 

Do you think maybe the new versions of Ubuntu and Kubuntu dont support something on this computer? Its not that old. 

Actually I am going to check one last thing... I was positive this is a 64bit computer, but widows 32 bit installed on it. So maybe its 32 bit and there lies the problem. Will feel quite dumb if so. WIll get back to you. 

Update: it is 64bit so thats not the issue. 

Thanks

---

### Post by amityweb on 2012-06-20
Think I will give up again for another year... I get this every year for the past 10 years when I try to setup a linux box. 

seem to get different errors. Just tried going back to Kubuntu and now get "end of file while reading invalid argument" after clicking Innstall now after choosing the partition.

---

### Post by amityweb on 2012-06-20
Can anyone recommend a a low cost compter/server with Linux on it already (e.g. Dell) and I might buy that as I assume it would all work then. I just need a development server for te office for web site development, dont need it for production or mission critical stuff, just a dev server.

Thanks

---

### Post by mastablasta on 2012-06-20
are you installing from CD? have you tried to install from USB?
 
does the live system work? what about if you use alternate CD or mini.iso?

---

### Post by mastablasta on 2012-06-20
> **amityweb said:**
> Can anyone recommend a a low cost compter/server with Linux on it already (e.g. Dell) and I might buy that as I assume it would all work then. I just need a development server for te office for web site development, dont need it for production or mission critical stuff, just a dev server.
 
Thanks
 
HP micro servers (but i don't know if they have enough power for you...)

---

### Post by amityweb on 2012-06-20
Installed from a CD and the live version works for both Kubuntu and Ubuntu. 

Probably wont need much power, be one or two people accessing it via SSH, FTP and HTTP, few dynamic websites (content managers). 

OH I have a backsup script that will run every night to backup other servers. 

So may not need much power.

---

### Post by darkod on 2012-06-20
Is this the 12.04 LTS Server you are trying to install?

It usually installs without problems, including few times in Virtual Box when I have tested it.
Is it possible that a sata cable to the disk is loose, or the disk going bad? That could produce input/output error, also the cd-rom can produce this error because while installing it is using the cd-rom as a device.
Can you test with an external usb cd-rom for example?

---

### Post by amityweb on 2012-06-20
I downloaded Ubuntu yesterday, so latest version, and Kubunto some time ago. 

I have a Sata drive, but I also added an IDE drive ( abrand new one because I thought I had drive issues) and had issues too. 

I will try the USB idea to rule out CD Rom issues and report back but wont be able to do it for a couple of days. 

Otherwise the HP server sounds OK, they dont cost too much. 

Thanks for all your help on this!

---

### Post by sudodus on 2012-06-20
> **amityweb said:**
> Installed from a CD and the live version works for both Kubuntu and Ubuntu. 

Probably wont need much power, be one or two people accessing it via SSH, FTP and HTTP, few dynamic websites (content managers). 

OH I have a backsup script that will run every night to backup other servers. 

So may not need much power.
Since live sessions work for you, I think that the CD drive is OK.

Maybe we can find something if you post the output of
```
sudo fdisk -lu
```

You might need to do something with your partitions.

---

