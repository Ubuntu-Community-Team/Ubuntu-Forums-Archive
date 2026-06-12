---
title: "Ubuntu-tweak download message &quot;STATUS : ERROR&quot;"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by Merel 469 on 2011-05-18
The third party program at [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) starts download (using Gdebi) and immediately displays an error message (in red) :

[COLOR="Red"][SIZE="2"]STATUS : ERROR: Dependency is not satisfiable : python (>=2.7)[/SIZE][/COLOR]

I had a look at the installed packages having "python" in their filenames, but they are numerous. This "mysterious" message does not suggest anything to overcome the problem !

Any idea what it means ? Any suggestion is welcome ; thank you.


I'm still reluctant to abandon Windows for Ubuntu, if this "operating" system (for human beings ?) is generating some problems, over and over again, at each occasion I'm working with,  :cry:

---

### Post by Merel 469 on 2011-05-18
[[IMG]http://img546.imageshack.us/img546/8840/screenshotpackageinstal.png[/IMG]](http://img546.imageshack.us/i/screenshotpackageinstal.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by drs305 on 2011-05-19
The error message means you need python version 2.7 or later. Natty has 2.71, Maverick uses 2.6.6 and Lucid 2.6.5.

You are probably getting the error message because you clicked on the 'Download' button, which attempted to install the latest version.

The best way to install GC is to add Mark Richter's repository to  your sources.list. You can easily do this with this command:
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```
Having the repository will allow your system to download the proper version as well as provide upgrades to your version when they become available.

Once you have enabled the repository you don't need to install it via command line, you can use any of the other methods (synaptic, software center, etc).

If this resolves your issue please mark the thread solved via the 'Thread Tools' link at the top right of the first post.

Happy Ubuntu-ing !  (and Ubuntu-Tweaking)

---

### Post by Merel 469 on 2011-05-19
Thank you **drs305** for this clear explanation. So far so good.
I managed to execute the command lines in sequence, without problem.

The results that I observed so far :

**1. In software sources**: 
a line with the stuff of PPA danielrichter has been added

**2. In Ubuntu software Center** 
> [Left Panel]"Get Software"
> [Select]"Launchpad PPA for Grub Customizer"
> [Right Panel]"Grub-customizer" **(installed !!??)**

This is very strange !!
The information is shown under the main menu title "GET SOFTWARE", (NOT under the main menu title "Installed Software" ; so I expected it to be some kind of "installer file" to be used for final installation. 

But actually **Grub-Customizer** **_WAS ALREADY installed !!!_**.
 
So, I unchecked a number of older kernels in this program.
But I don't know yet if this only removes entries from the list, or if the old kernels are being (or will be) un-installed at the next boot. Wait and see.

As for installation of "Ubuntu-Tweak" package, I will have a further look.

I will come back for further comments.

---

### Post by Merel 469 on 2011-05-21
To install Ubuntu-Tweak on Ubuntu 10.4 LTS 

Follow steps :

1. Execute commands indicated by **drs305** to install Grub Cutomizer

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

2. Once this is done, you can proceed to install Ubuntu-Tweak 0.5.13-1 by a download at [www.ubuntu-tweak.com](www.ubuntu-tweak.com).

There is a message "All dependencies are satisfied"
The installation requires little time and is without further mandatory preliminary action.


Thank you, **drs305**

---

### Post by c0rrupt0r on 2011-05-26
I had this same problem with downloading ubuntu tweak and that is because they have it set to download for natty version. if your using maverick then you will need to go here and download the one for maverick [https://launchpad.net/ubuntu-tweak/+download](https://launchpad.net/ubuntu-tweak/+download) Installs flawless for me

---

### Post by Parikx on 2011-06-10
> **c0rrupt0r said:**
> I had this same problem with downloading ubuntu tweak and that is because they have it set to download for natty version. if your using maverick then you will need to go here and download the one for maverick [https://launchpad.net/ubuntu-tweak/+download](https://launchpad.net/ubuntu-tweak/+download) Installs flawless for me

Cool the link above worked like a charm!

---

### Post by Gyanos422 on 2011-07-09
this also worked for me on Lucid. had to find appropriate version. it should auto detect version when downloading from ubuntu tweak homepage

---

