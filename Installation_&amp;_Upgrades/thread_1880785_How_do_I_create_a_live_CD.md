---
title: "How do I create a live CD?"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by glennbates on 2011-11-14
Unfortuanantly, I am using Windows 7.  I am unable to create a live CD.  When I try, and seems successful, I try to boot from the CD and all I get is the ability to install it somewhere else.

---

### Post by dino99 on 2011-11-14
you have live-magic into synaptic to do a cd.

---

### Post by mörgæs on 2011-11-14
Which ISO are you using?

---

### Post by glennbates on 2011-11-14
> **mörgæs said:**
> Which ISO are you using?
 I have tried both 
 
ubuntu-10.04.3-server-amd64
 
& 
 
ubuntu-10.04.3-server-i386

---

### Post by MG&amp;TL on 2011-11-14
[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

---

### Post by glennbates on 2011-11-14
> **MG&TL said:**
> [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
 Here's the problem.  This, and many other helps I read say "Right-click on an ISO image and choose 'Burn disc image'. "  On my computer, with Windows 7, there is no option "Burn disc image".

---

### Post by mörgæs on 2011-11-14
The server ISO does not run in a live boot. Only the desktop ISO has this option.

---

### Post by glennbates on 2011-11-14
> **mörgæs said:**
> The server ISO does not run in a live boot. Only the desktop ISO has this option.
 Oh, ok.  Thanks.

---

### Post by philinux on 2011-11-14
> **glennbates said:**
> Here's the problem.  This, and many other helps I read say "Right-click on an ISO image and choose 'Burn disc image'. "  On my computer, with Windows 7, there is no option "Burn disc image".

I just checked on my win 7 laptop and the right click option has Burn disk image as the first item. :confused:

Also "open with" has Windows Disk Image Burner recommended.

Maybe check if it's installed. Or use a third party one.

---

### Post by glennbates on 2011-11-14
> **philinux said:**
> I just checked on my win 7 laptop and the right click option has Burn disk image as the first item. :confused:
 
Also "open with" has Windows Disk Image Burner recommended.
Windows 7 must be different for each day they put it out.  Interesting.

---

### Post by MG&amp;TL on 2011-11-14
I think it might be different depending on the version you have. I think 'home premium' and above has it.

---

### Post by mörgæs on 2011-11-14
If this solved your problem, please mark the thread so.

---

### Post by glennbates on 2011-11-14
> **mörgæs said:**
> If this solved your problem, please mark the thread so.
 Well, I'm not sure it has.  I'm still using Windows.  :(

---

### Post by Hakunka-Matata on 2011-11-14
If you are still using Windows, the ***problem*** has not been SOLVED.  Sorry, couldn't resist..... good luck

---

### Post by glennbates on 2011-11-14
> **Hakunka-Matata said:**
> If you are still using Windows, the ***problem*** has not been SOLVED. Sorry, couldn't resist..... good luck
 I agree.  Thanks

---

### Post by MG&amp;TL on 2011-11-14
Could you reiterate what your problem is? If you can't use windows disk burner, use infra recorder, it's free software. Or use unetbootin and a USB.

---

### Post by Hakunka-Matata on 2011-11-14
free CD burners for windows OSs
[http://download.cnet.com/windows/cd-burners/](http://download.cnet.com/windows/cd-burners/)

Status report please:  What do you need?  anything?

---

### Post by glennbates on 2011-11-14
> **Hakunka-Matata said:**
> free CD burners for windows OSs
[http://download.cnet.com/windows/cd-burners/](http://download.cnet.com/windows/cd-burners/)
 
Status report please: What do you need? anything?
 Mainly, I need to dual boot my computer with Ubuntu.  I don't know what else to try.  The few times I was able to install it on here, it only went to a terminal prompt. I keep starting over but no success.  I'm trying to think of how else I can do it.

---

### Post by MG&amp;TL on 2011-11-14
You can try wubi. Or virtualbox, if your hardware isn't playing nicely.

---

### Post by Hakunka-Matata on 2011-11-14
How about your HD partitioning and free space available, etcetera.  Can you post a picture of your HD's layout?  Use Windows Disk Manager and post a picture.
You have not really said much about how the problem presents itself, when?, do you have a CD that's working now?, What does the directory of files on the CD look like?, can you post the directory listing?

---

### Post by glennbates on 2011-11-14
> **MG&TL said:**
> You can try wubi. Or virtualbox, if your hardware isn't playing nicely.
 wubi only allows me to format the c: drive.  There is no partition option.

---

### Post by glennbates on 2011-11-14
Some how, I had a double post.  How do I delete this one?

---

### Post by glennbates on 2011-11-14
My reply keeps getting deleted. What's going on?
 
Then it shows up after I post again.

---

### Post by MG&amp;TL on 2011-11-15
Don't know, I'm sure nobody minds too much. :)

How far do you get into the install process before you have a problem?

---

### Post by glennbates on 2011-11-15
I'm not real worried about creating the live CD.  I just want to install a working environment with Ubuntu.  It seems to install properly but when I boot to the Ubuntu that I install, all I get is, I guess, a terminal prompt.  Looks like the DOS computer from the early 90's.

---

### Post by MG&amp;TL on 2011-11-15
Oh. Like this:

```
user@computername:~$
```

??

If so, you've got the command-line install. :D If you are after a desktop, you want the normal install of the ubuntu site, not ubuntu server or whatever.

From here:  [http://www.ubuntu.com/download/ubuntu/download]("http://www.ubuntu.com/download/ubuntu/download")

---

### Post by glennbates on 2011-11-15
> **MG&TL said:**
> Oh. Like this:
 
```
user@computername:~$
```
 
??
 
If so, you've got the command-line install. :D If you are after a desktop, you want the normal install of the ubuntu site, not ubuntu server or whatever.
 
From here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
I've tried that one also. 32 and 64 bit. 11.10 and 11.04. Server and non server. I've tried all 8 of them. I always get the same thing.
 
While installing, I get:
 
Network autoconfiguration failed
Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly.
 
 
Could this be part of the problem?
 
Would a different version of Ubuntu be better?  Xubuntu or something?  Remember, I mainly want it for building web sites so I want LAMP to be installed.

---

### Post by Hakunka-Matata on 2011-11-15
If your machine won't connect to the Internet, that would present a fairly big speed bump,
where should it be getting it's Network adapter IP address from?  A local DHCP server, like your wireless router?  or from your ISP if you're plugged directly into the ISP router

---

### Post by glennbates on 2011-11-15
> **Hakunka-Matata said:**
> If your machine won't connect to the Internet, that would present a fairly big speed bump,
where should it be getting it's Network adapter IP address from? A local DHCP server, like your wireless router? or from your ISP if you're plugged directly into the ISP router
 I'm connected to a wireless router.  This is a laptop.

---

### Post by Hakunka-Matata on 2011-11-15
and you're posting from a windows OS?

Have you ever gotten Ubuntu liveCD, USB, whatever to boot on that laptop?

---

### Post by glennbates on 2011-11-15
> **Hakunka-Matata said:**
> and you're posting from a windows OS?
 
Have you ever gotten Ubuntu liveCD, USB, whatever to boot on that laptop?
 I had 11.04 on here.  It was running great.  I upgraded to 11.10 and all I got was a blank screen.  I tried to reinstall and it has not worked since.

---

### Post by glennbates on 2011-11-15
SUCCESS!!!!!  I am now back to using Ubuntu.  Not only that, I have 11.10 and 64 bit where I did have 11.04 and 32 bit.  Now to reinstall what I had, especially LAMP.  Now to go back and read all of the threads that helped me before.


Thanks everyone!!!

---

### Post by MG&amp;TL on 2011-11-16
No problem, pleased you got it in the end. Have you seen this?

[https://help.ubuntu.com/community/ApacheMySQLPHPhttps://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHPhttps://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by glennbates on 2011-11-16
> **MG&TL said:**
> No problem, pleased you got it in the end. Have you seen this?

[https://help.ubuntu.com/community/ApacheMySQLPHPhttps://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHPhttps://help.ubuntu.com/community/ApacheMySQLPHP)
Interesting.  What does it do?

---

### Post by MG&amp;TL on 2011-11-16
I'm assuming you want a LAMP stack back (as in, Linux Apache MySQL PHP). That's how you set it up in Ubuntu. :D

Community docs have interesting stuff in. Have a look at some point.

---

### Post by glennbates on 2011-11-16
> **MG&TL said:**
> I'm assuming you want a LAMP stack back (as in, Linux Apache MySQL PHP). That's how you set it up in Ubuntu. :D

Community docs have interesting stuff in. Have a look at some point.
Thanks.  I already have it installed.  That was the first thing I did.

Thanks again!

---

