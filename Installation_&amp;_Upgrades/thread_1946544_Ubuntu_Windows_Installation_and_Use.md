---
title: "Ubuntu Windows Installation and Use"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by ramin1 on 2012-03-25
Hi everyone here's what I want to do:

I want to Install Ubuntu Server on my Windows Laptop and run it.

in a simple steps which would not give me any errors would you please tell me how? 

Here's some hardware and software info about my laptop:
just in case if its necessary:

its running windows vista the Home Premium
its service pack 2
2 GB ram
its 32 bit operating system
Processor: Genuine Intel(R) CPU    T2250 @ 1.73 GHz 1.73GHz

so I need help big time I tried to download Ubuntu Server and burned it on CD but that was for Linux and I tried also downloading the windows installer, it keeps telling me that there's no CD in the drive which I had it already running in the drive. So I dont know whats the legitimate way to successfully install UBUNTU SERVER with no problems. Please Please Help.

---

### Post by gordintoronto on 2012-03-25
Ubuntu Server is Linux. It's not clear what you want to do. You can either run Windows, or you can run Linux.

Perhaps the best thing would be for you to read a little more.

---

### Post by darkod on 2012-03-25
Do you plan to replace windows or dual boot? Usually you wouldn't dual boot a server OS because you want the server to run all the time.

Anyway, to install the server OS you need to download the server iso image (32bit or 64bit as you wish) and burn a cd with that image. Make sure you burn a cd from the image, not simply the iso file on the cd as a file. You can do this on windows computer, doesn't matter.

Then you need to boot with this cd and start the server install. Look for tutorials on google if you need more info.

If you are planning to dual boot with windows first make sure you have unpartitioned space on the hdd. Make sure you shrink any windows partition first if you need to.

---

### Post by collisionystm on 2012-03-25
You need to use an .ISO burner to put it on a disk. Sounds to me like you are simply just placing the iso file itself on it.

I always use

isorecorder.alexfeinman.com

or 

[http://infrarecorder.org/](http://infrarecorder.org/)

---

### Post by Mark Phelps on 2012-03-26
> **ramin1 said:**
> ... I want to Install Ubuntu Server on my Windows Laptop and run it....So I dont know whats the legitimate way to successfully install UBUNTU SERVER with no problems. Please Please Help.

You sure you know what you're getting into?

Server is a command-line setup with no GUI desktop.

If you know so little about command line actions that you need step-by-step failsafe instructions to INSTALL a server, how are you then going to use it afterward?

Also, that machine is majorly underpowered to function as a real server.  So are you intending to use it for that purpose? OR are you only interested in experimenting with a server version?

---

### Post by collisionystm on 2012-03-26
Its really not that under-powered.

A vanilla install of server only eats about 100mb of ram or less.

Its a 64 bit CPU he has. 

I agree running it on a laptop is not the norm, but the OP should be okay.

---

