---
title: "[SOLVED] OpenOffice2.3 Upgrade in Feisty"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by k3lt01 on 2007-10-28
I want to upgrade my OpenOffice version in Feisty to 2.3. I cannot do it through Synaptic as it is not supported in Feisty. I have the files downloaded from OpenOffice.org and have them extracted into a folder in my home directory. My question is how do I installed it? I have clicked on the deb files but I keep getting dependency issues, for every one. I know there are scripts to update Firefox and Thunderbird beyond what is supported in Feisty, I was hoping there may be scripts to do the same for OpenOffice.

I will ask one other thing. Please don't tell me to upgrade to Gutsy, I have tried that already and I could not get my internet access working at all. I won't be trying Gutsy again for a fair while because of the apparent bugs regarding network access.

Thanks in advance.
Michael.

---

### Post by arkangel on 2007-10-28
uninstall all  openoofice  stuff  you have , (use for example sinaptic  to locale it ,  look for the meta package  , open office  commont , etc )  now you are clean

install alien  so the installer will be able to convert the *rpm into *deb   ,  open a console
 > 
$sudo aptitude install alien  debhelpe dpkg-dev dpkg 

extract the  files.      In a console   go to the installation folder 
> cd  /where_ever_you_extact/OOG680_m5_native_packed-1_en-US.9221

 and then  type  
> sudo  ./setup 

a java  window will  pop up ,  follow the instructions ...

---

### Post by PmDematagoda on 2007-10-28
Do:-

```
sudo dpkg-i *.deb
```

in the folder containing the .deb's.

But I would recommend uninstalling the OpenOffice already present before doing the upgrade.

---

### Post by k3lt01 on 2007-10-28
> **arkangel said:**
> uninstall all  openoofice  stuff  you have , (use for example sinaptic  to locale it ,  look for the meta package  , open office  commont , etc )  now you are clean. Tried that after I posted still did not work

> **arkangel said:**
> install alien  so the installer will be able to convert the *rpm into *deb   ,  open a console. They are already .deb files
 

> **arkangel said:**
> a java  window will  pop up ,  follow the instructions ... The only thing that pops up is package installer and it tells me I have dependency problems.

> **PmDematagoda said:**
> Do:-

```
sudo dpkg-i *.deb
```

in the folder containing the .deb's.. So I use the Terminal and cd to my home/michael/Computer/OOG680_m5_native_packed-1_en-US.9221/DEBS/ folder and do sudo dpkg-i *.deb and it should work.

> **PmDematagoda said:**
>  But I would recommend uninstalling the OpenOffice already present before doing the upgrade. I uninstalled them after I posted the first post, and when I couldn't install 2.3 I reinstalled them. I will try again in the morning.

Thanks for the help guys. :) Will let you know what happens.

How do I mark the thread as solved if it works?

---

### Post by rahimveron on 2007-10-28
> **k3lt01 said:**
> How do I mark the thread as solved if it works?
Just Click on "Thread Tools" on the upper-right on your thread and you will have an option"Marked as Solved" or something like that.
Regarding your OO upgrade, do you have a folder named "Desktop Integration " in your RPMS folder?

---

### Post by cetheriel on 2007-10-28
why dont you try the backport repository? it is an option under "software sources", it should alow you to install gutsy packages on feisty.... i installed decibel on feisty that way...

---

### Post by PmDematagoda on 2007-10-28
> So I use the Terminal and cd to my home/michael/Computer/OOG680_m5_native_packed-1_en-US.9221/DEBS/ folder and do sudo dpkg-i *.deb and it should work.

Yes, that is one stage, after that, there is another package found in a folder of the DEBS folder, install that after OpenOffice installation to setup the menu icons.

---

### Post by rahimveron on 2007-10-28
> **PmDematagoda said:**
> Yes, that is one stage, after that, there is another package found in a folder of the DEBS folder, install that after OpenOffice installation to setup the menu icons.

Thats why i asked him about the folder desktop integration that cntains deb of the menus

---

### Post by k3lt01 on 2007-10-28
> **rahimveron said:**
> Just Click on "Thread Tools" on the upper-right on your thread and you will have an option"Marked as Solved" or something like that.
Regarding your OO upgrade, do you have a folder named "Desktop Integration " in your RPMS folder?
There is a folder named "Desktop Intergration" but there is no RPMS folder, it is within the DEBS folder along with the majority of the .debs.

Thanks for the info.

---

### Post by k3lt01 on 2007-10-28
Here is what happened

```
michael@michael-laptop:~$ cd /home/michael/Computer/OOG680_m5_native_packed-1_en-US.9221/DEBS/ 
michael@michael-laptop:~/Computer/OOG680_m5_native_packed-1_en-US.9221/DEBS$ sudo dpkg-i *.deb
Password:
sudo: dpkg-i: command not found
michael@michael-laptop:~/Computer/OOG680_m5_native_packed-1_en-US.9221/DEBS$

```

Is it looking for something that is not there? the folder is how it was downloaded from OpenOffice.org

Tried the backport hint, didn't work either.

What am I doing wrong?

---

### Post by rahimveron on 2007-10-29
> **k3lt01 said:**
> ```
michael@michael-laptop:~/Computer/OOG680_m5_native_packed-1_en-US.9221/DEBS$ sudo dpkg-i *.deb
```?
The install command you entered is a typo. Enter this command```
sudo dpkg -i *.deb
```
There should be a space after dpkg and then -i
Another point have you got this deb openoffice.org-debian-menus_2.3-9215_all.deb in Desktop Integration folder? This will put OO in the Menus.

---

### Post by k3lt01 on 2007-10-29
Yes that .deb was in the folder.

Everything is installed now, thanks Rahimveron and everyone else who gave suggestions.

---

### Post by Nda on 2007-11-17
This isn't working for me.  I have downloaded and extracted OpenOffice.org 2.3 to a folder on my Desktop.  I had a look and there is a folder DEBS in there, so I did cd into the folder:

```
nda@mobile:~$ cd /home/nda/Desktop/OOG680_m5_native_packed-1_en-US.9221/DEBS
```and then:

```
sudo dpkg -i *.deb
Password:
```only to get this:

```

dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
```Now I'm stuck.  Does anyone have any suggestions as to what is going wrong and how I can make it work?

Nda

---

### Post by k3lt01 on 2007-11-17
> **Nda said:**
> This isn't working for me.  I have downloaded and extracted OpenOffice.org 2.3 to a folder on my Desktop.  I had a look and there is a folder DEBS in there, so I did cd into the folder:

```
nda@mobile:~$ cd /home/nda/Desktop/OOG680_m5_native_packed-1_en-US.9221/DEBS
```and then:

```
sudo dpkg -i *.deb
Password:
``` Try this 
```
 cd Desktop/OOG680_m5_native_packed-1_en-US.9221/DEBS/
```
then ```
sudo dpkg -i *.deb
```

I think you have gone the long way about and left off  / after DEBS. Hope this helps, let us know how you go.

---

### Post by Nda on 2007-11-19
k3lt01,

It was of course the trailing "/" after DEBS that I had overlooked.  Many thanks for spotting that.

I now have a fully-functioning OO.o 2.3, complete with shiny new icons in the menu.  Very pleased.

Nda

---

### Post by k3lt01 on 2007-11-19
Excellent.

I like OOo alot, so much so I am not using MS Office anymore even on my remaining Windows machine.

---

