---
title: "Installing/Unistalling Programs"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by ThatNewGuy on 2013-05-20
Hello Ubuntu Community,

I am new here and I was hoping someone could point me in the right direction here. I am trying to better understand installing/uninstalling programs through the terminal & by downloading and installing like you would on a windows OS.
If someone could post me a link to a good thread on this, Its greatly appreciated.

I have currently Ubuntu 12.10 full install on my desktop. 

Thank you,
ThatNewGuy

---

### Post by Frogs Hair on 2013-05-20
Hello and Welcome,

You can start in the terminal with the following and see my signature for Ubuntu documentation   ```
man dpkg 
```

---

### Post by grahammechanical on 2013-05-20
In Linux we do not do things the Microsoft way. So, do not expect to find an Add/Remove programs utility. Or the need to browse to an install.exe file or setup.exe file.
 
In Ubuntu we have the Software Centre to do that. We can also use Synaptic Package Manager to install and remove applications (Synaptic is not installed by default). There is also an Update Manager to update the OS. Synaptic will also do the same. These utilities are front ends for a command called apt-get.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards.

---

### Post by oldos2er on 2013-05-20
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://www.howtogeek.com/63997/how-to-install-programs-in-ubuntu-in-the-command-line/](http://www.howtogeek.com/63997/how-to-install-programs-in-ubuntu-in-the-command-line/)

---

### Post by ThatNewGuy on 2013-05-20
Thank you for your help, now I figured out my issue here. So i did go and install synaptic and i see thats how you install programs not using the terminal or you can use the terminal from sudo apt-get install synaptic command. while I did read through the links Im now more curious. This is my main issue, i tried just typing "sudo apt-get install adobe reader" but nothing happends because its not in the SPM. I google it and its " sudo apt-get install acroread" my question is how does one know to type it this way. same for flash player and java editors etc.  Im so puzzled by this.

---

### Post by Mark Phelps on 2013-05-20
Actually, you're doing it the hard way by using the terminal -- which requires that you KNOW what you're doing!

Using the much easier way (Software Center), you can do searches for things to install, and it will present the proper packages for you.

---

### Post by ThatNewGuy on 2013-05-20
oh oK ill do my reasearch on that then.

---

### Post by oldos2er on 2013-05-20
> **ThatNewGuy said:**
> Thank you for your help, now I figured out my issue here. So i did go and install synaptic and i see thats how you install programs not using the terminal or you can use the terminal from sudo apt-get install synaptic command. while I did read through the links Im now more curious. This is my main issue, i tried just typing "sudo apt-get install adobe reader" but nothing happends because its not in the SPM. I google it and its " sudo apt-get install acroread" my question is how does one know to type it this way. same for flash player and java editors etc.  Im so puzzled by this.

Packages aren't "in" Synaptic, which is just a graphical front-end to APT (same as Software Center); they're in the repositories which are listed in /etc/apt/sources.list and possibly in *.list files in /etc/apt/sources.list.d/ too.

If you want to search for packages in terminal, you can use ```
apt-cache search <search term>
``` If I run ```
apt-cache search adobe reader
``` I get the following: 
```
texlive-latex-extra - TeX Live: LaTeX supplementary packages
bleachbit - delete unnecessary files from the system
epubcheck - ePub book format validator
ruby-pdf-reader - Ruby library for accessing the content of PDF files
xpdf - Portable Document Format (PDF) reader
acroread - Adobe Reader
adobereader-deu - Adobe Reader
adobereader-fra - Adobe Reader
adobereader-jpn - Adobe Reader
acroread-common - Adobe Reader - Common Files
acroread-bin - Adobe Reader
``` If I then want more information on the package 'acroread,' I'd type ```
apt-cache show acroread
``` But like Mark said, you might want to stick with Software Center, or Synaptic, until you become more familiar with things.

---

### Post by ThatNewGuy on 2013-05-24
Thank you for all your help, Its been very helpful.

---

