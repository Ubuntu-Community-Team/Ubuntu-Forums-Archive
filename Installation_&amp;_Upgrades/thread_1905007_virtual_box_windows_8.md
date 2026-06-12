---
title: "virtual box windows 8"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by Alphamonkey on 2012-01-05
Hi, was just wondering if anyone knows if I can get the "development release" of windows 8 to run in virtual box. I downloaded the ISO for it but I don't actually want to install it on my pc. Just curious about their new and "improved" interface. looks like it would be very difficult to use to me but like I said I am curious about it.

---

### Post by Paddy Landau on 2012-01-06
If you have the ISO, why don't you just try installing it in Virtual Box? You will find out quickly whether or not it will install.

---

### Post by Mark Phelps on 2012-01-06
A quick Google found the link below:

[http://www.addictivetips.com/windows-tips/how-to-install-windows-8-on-virtualbox/]("http://www.addictivetips.com/windows-tips/how-to-install-windows-8-on-virtualbox/")

If you have other Win8 questions, you should go to the Win8 forum: eightforums.com

---

### Post by Alphamonkey on 2012-01-07
the problem I am having is that my computer is unable to read the udf format. 

"This disc contains a "UDF" file system and requires an operating system 
that supports the ISO-13346 "UDF" file system specification."

so I guess I really just need to figure out how to get the udf file system to work on my computer, however the usual way I have found online hasn't worked. where you switch from 9660 to auto.

---

### Post by clicklisa on 2012-01-07
```
sudo apt-get install libudf0
```

---

### Post by Alphamonkey on 2012-01-07
> **clicklisa said:**
> ```
sudo apt-get install libudf0
```

I already installed that package yesterday. Thanks for the suggestion though.

---

### Post by Paddy Landau on 2012-01-07
Googling your problem, there seem to be several programs that convert UDF to ISO, but only in Windows. If you have access to Windows, you could try that.

Or, the only Linux program that I have come across that may work (but I can't promise it) is [Iso9660 Analyzer Tool (iat)]("apt:iat"). Install it, and then run the following, where [source] is your UDF file and [target] is the name of the file you'd like to create.
```
iat [source] [target].iso
```There is also an option to mount UDF formats, apparently. I found a link showing [how to mount UDF DVDs in Ubuntu]("http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu/"), but in your case this is a file, not a DVD. So, on the basis of experimentation, try this, where [mountpoint] means an *empty* directory in which to mount the UDF file.
```
sudo mount --options ro,loop [source] [mountpoint]
```If that doesn't work, try this:
```
sudo mount --types udf --options ro,loop [source] [mountpoint]
```Let us know what happens.

---

### Post by goldshirt9 on 2012-01-07
i have installed and run Windows 8 in Virtual box.Runs great
Unfortunately i never had this error.

---

### Post by Paddy Landau on 2012-01-08
Out of curiosity, I downloaded the Windows 8 Developer Preview, and I am trying to install it on VB.

VB had no problem whatsoever recognising the ISO file. Which version of Virtual Box are you using that it cannot recognise the ISO?

However, after starting up the installation, it has sat there doing nothing (not even twirling the little circle -- see screen shot) for 20 minutes already, with two CPU cores both running at 100%. For how long do you think I should wait until I decide that it's just not going to progress any further? (I gave it 2Gb RAM as recommended by Microsoft.)

---

### Post by Alphamonkey on 2012-01-08
> **Paddy Landau said:**
> Out of curiosity, I downloaded the Windows 8 Developer Preview, and I am trying to install it on VB.

VB had no problem whatsoever recognising the ISO file. Which version of Virtual Box are you using that it cannot recognise the ISO?

However, after starting up the installation, it has sat there doing nothing (not even twirling the little circle -- see screen shot) for 20 minutes already, with two CPU cores both running at 100%. For how long do you think I should wait until I decide that it's just not going to progress any further? (I gave it 2Gb RAM as recommended by Microsoft.)


the problem doesn't actually lie with VB. My linux is unable to recognize the UDF formart.

---

### Post by Paddy Landau on 2012-01-09
> **Mark Phelps said:**
> [http://www.addictivetips.com/windows-tips/how-to-install-windows-8-on-virtualbox/](http://www.addictivetips.com/windows-tips/how-to-install-windows-8-on-virtualbox/)
Thanks, Mark, that helped me.

> **Alphamonkey said:**
> the problem doesn't actually lie with VB. My linux is unable to recognize the UDF formart.
I have tried both the SATA and IDE controllers (on VB) for my downloaded ISO, and both of them are happy with it. May I ask:

[LIST]
[*]Which version of Ubuntu are you using?
[LIST]
[*]And is it fully up-to-date?
[/LIST]
 
[*]Which version of VB are you using?
[LIST]
[*]And have you installed its Extension Pack?
[/LIST]
 
[*]Which Windows 8 Developer Preview did you download (there are [three different ones on the MSDN site]("http://msdn.microsoft.com/en-us/windows/apps/br229516"))?
[LIST]
[*]After downloading, did you check the SHA1 hash?
[/LIST]
 
[*]How are you mounting the ISO in your virtual machine? (The correct way is to go to the virtual machine that you have set up > Settings > Storage > [s]*either*[/s] IDE Controller [s]*or* SATA Controller[/s] > *click the button that shows* Add CD/DVD Device > Choose Disk > *choose your ISO*.)
[/LIST]
**EDIT:** I made a mistake with choosing the ISO; it must be the IDE Controller.

---

