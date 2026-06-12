---
title: "How to install a tar.gz file from command line"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by malangbaba on 2010-01-07
I did a command-line installation.

I dont have an ethernet connection, only wireless.
For some reason the alternate installer doesnt install "wireless-tools"

How do install it?
At this point I am thinking of botting off a live USB, downloading the wireless-tolls package from [here]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html")
Save it to a folder in the command line installation (where?)
then boot back into command line and install from there

But I am not that savvy with command lines, and dont know where to install to...

thoughts?

---

### Post by Revolutionary101 on 2010-01-07
A tar.gz file is not an installation file, it is just a compressed file (just like .zip). To install it just extract the files to a folder and run the program. In most cases installation is not required.

---

### Post by malangbaba on 2010-01-07
sorry, i know a tar.gz file is a compressed file.
but your point about likeliness that no installation required is taken...

let me try...

thanks!

---

### Post by malangbaba on 2010-01-07
ok, i got the file download. untar'ed it.

I do a "sudo make install"
but it tells me:
make: gcc: command not found

Will try to download gcc the same way now

---

### Post by warfacegod on 2010-01-07
Tell the terminal to navigate to the folder you extracted:


```
cd /someplace/another/etractedfloder
```


Next, I believe this is right:


```
sudo apt-get install completefilename
```

---

### Post by malangbaba on 2010-01-07
Hmmm...doing that just tells me package not found. even though I am in containing directory

---

### Post by warfacegod on 2010-01-07
I think the name needs to be exact. Then back up one folder.

---

### Post by malangbaba on 2010-01-07
yes im sure the name would need to be exact :)
it still didnt work
not even in my working installation on another laptop

---

### Post by AlexandreP on 2010-01-07
> **warfacegod said:**
> Tell the terminal to navigate to the folder you extracted:


```
cd /someplace/another/etractedfloder
```


Next, I believe this is right:


```
sudo apt-get install completefilename
```

*apt-get* works with packages from a packages repository. It does not work with local/manually downloaded .deb files *(use Gdebi or dpkg to install them)* nor with .tar.gz/.zip/.tar.bz2/etc compressed files *(which usually contain source code that has to be compiled)*.

> **malangbaba said:**
> I do a "sudo make install"
but it tells me:
make: gcc: command not found

Will try to download gcc the same way now
You have to install some additionnal software if you want to compile programs. The package [build-essential](apt://build-essential) (from your packages manager) should install the basic stuf needed. (I don't know if it is present in Ubuntu CD-ROM, though. You may need the get an Internet connection in order to install it.)

But don't forget to take a look at a README or INSTALL file that is included in the .tar.gz archive. It may well contain some interesting information about how to install this software (need anything special? how to compile? does it need to be compiled? etc.).

---

### Post by malangbaba on 2010-01-07
> **AlexandreP said:**
> *apt-get* works with packages from a packages repository. It does not work with local/manually downloaded .deb files *(use Gdebi or dpkg to install them)* nor with .tar.gz/.zip/.tar.bz2/etc compressed files *(which usually contain source code that has to be compiled)*.

Yeah, this is what I have gotten to...looked up .deb files for wireless-tools and gcc online through a liveUSB.  downloaded them to hardrive. rebboted and tried dpkg.

But it still gives errors, i think maybe for dependencies...will check it again in a bit...


> **AlexandreP said:**
> You have to install some additionnal software if you want to compile programs. The package [build-essential](apt://build-essential) (from your packages manager) should install the basic stuf needed. (I don't know if it is present in Ubuntu CD-ROM, though. You may need the get an Internet connection in order to install it.)

I am getting online through a liveUSB. downloading that way. but so far have to do the files one by one, and when i go back to command line i learn i need another dependency

> **AlexandreP said:**
> But don't forget to take a look at a README or INSTALL file that is included in the .tar.gz archive. It may well contain some interesting information about how to install this software (need anything special? how to compile? does it need to be compiled? etc.).

dependencies issues would be the same whether i install off of .deb or compile from source, ya?

---

### Post by malangbaba on 2010-01-07
Is there a way for me to maybe download the DVD onto a usbdrive and then access all the packages from there?

---

### Post by AlexandreP on 2010-01-07
> **malangbaba said:**
> dependencies issues would be the same whether i install off of .deb or compile from source, ya?
Yes. Even if you are compiling the program, you may need some other things from the repos.

*dpkg* does not download dependencies (it assumes you already have downloaded and installed them).

---

### Post by AlexandreP on 2010-01-07
> **malangbaba said:**
> Is there a way for me to maybe download the DVD onto a usbdrive and then access all the packages from there?
Well, yes, you can download Ubuntu's DVD ISO image into your USB drive, then mount it using *mount* and add it in Synaptic (in Synaptic, go to *Settings -> Repositories -> Other software -> **Add CR-ROM***).

---

### Post by malangbaba on 2010-01-07
> **AlexandreP said:**
> Well, yes, you can download Ubuntu's DVD ISO image into your USB drive, then mount it using *mount* and add it in Synaptic (in Synaptic, go to *Settings -> Repositories -> Other software -> **Add CR-ROM***).

Can I do this through a command line installation?
And would I  just copy the .iso to the USB or make a bootable USB of the DVD?

---

### Post by malangbaba on 2010-01-08
SOLVED!

Went and got the wireless-tools, libc6 (udev), libiw29 packages from packages.ubuntu.com

installed them on CL through dpkg

got wireless-tools on

now wireless works!

---

