---
title: "Intrepid beta doesn't have OpenOffice 3?"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by yosumi on 2008-10-21
i ran the beta live cd but it doesn't have openoffice 3. it should have openoffice 3 in the final build?

---

### Post by olskar on 2008-10-21
> **yosumi said:**
> i ran the beta live cd but it doesn't have openoffice 3. it should have openoffice 3 in the final build?

No :( But it will come in backports

---

### Post by fballem on 2008-10-21
To install Open Office 3.0 using software that is obtained from [http://www.openoffice.org](http://www.openoffice.org) directly, do the following:

- Uninstall the existing installation of Open Office 2.4 software (this is a really long command string - please make sure you get all of it):

```
sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer

```
- Change to the folder containing the download archive and extract the files from the archive:

```
cd ~/Desktop
tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
cd OOO300_m9_native_packed-1_en-US.9358/DEBS

```
- Install OpenOffice:

```
sudo dpkg -i *.deb
```

- Intall the OpenOffice menus. This can only be done if OpenOffice 2.4 was removed:

```
sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb

```

Hope this helps,

---

### Post by Kow on 2008-10-21
> **fballem said:**
> To install Open Office 3.0 using software that is obtained from [http://www.openoffice.org](http://www.openoffice.org) directly, do the following:

- Uninstall the existing installation of Open Office 2.4 software (this is a really long command string - please make sure you get all of it):

```
sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer

```
- Change to the folder containing the download archive and extract the files from the archive:

```
cd ~/Desktop
tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
cd OOO300_m9_native_packed-1_en-US.9358/DEBS

```
- Install OpenOffice:

```
sudo dpkg -i *.deb
```

- Intall the OpenOffice menus. This can only be done if OpenOffice 2.4 was removed:

```
sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb

```

Hope this helps,

Is it not 100x better to use
[http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
? This includes all of the ubuntu patches.

---

### Post by shane19174 on 2008-10-21
> Is it not 100x better to use
[http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
? This includes all of the ubuntu patches.

I would also think so. Especially when you consider that removing OOo 2.4 also removes ubuntu-desktop!

---

### Post by int on 2008-10-21
It's better to use Kow way.. Because include more 500 patchs..

---

### Post by plun on 2008-10-21
Yup, Calcs ppa is also broken, Extensions and updates, also RC4.

fballems manual brakes Ubuntu-desktop. I have them installed parallell.

Other good manuals for the real version:

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)


Just incredible to skip OO-3...:confused::(

---

### Post by shane19174 on 2008-10-21
> Yup, Calcs ppa is also broken

What do you mean? I just upgraded for the second time (i.e. on a second machine) last evening from calc's repo, and everything went fine. How is it broken?

Thanks,
Shane

---

### Post by Kow on 2008-10-21
BTW the repos I posted will be what the official backport is based off. The OO Ubuntu devs are using that repository for their current working 3.0 tree. I don't think they've updated the tree since OO 3.0 final (RC4) was released so it must be stable. I know I have not had any issues with it.

---

### Post by plun on 2008-10-21
> **shane19174 said:**
> What do you mean? I just upgraded for the second time (i.e. on a second machine) last evening from calc's repo, and everything went fine. How is it broken?

Thanks,
Shane

Its RC4 within calcs repo, he also wrote it within a message somewhere

Extensions are broken, also probably updates.

[http://extensions.services.openoffice.org/](http://extensions.services.openoffice.org/)

Wrong colors and other minor issues compared with final.

The splash for example is yellow in calcs repo and blue in final...

---

### Post by shane19174 on 2008-10-21
> Its RC4 within calcs repo, he also wrote it within a message somewhere

Extensions are broken, also probably updates.

OK, thanks for the clarification. I had noticed the yellow splash, but I didn't think anything of it. And I'm not working with any extensions at the moment. So I think I'll stick with calc's ppa until the backports are ready so I don't have to uninstall ubuntu-desktop.

---

### Post by fballem on 2008-10-21
I am using ubuntu 8.10 beta. I'm not sure if this works on Hardy, but after completing the installation according to my instructions,

```
sudo apt-get install gnome-desktop-environment
```

will restore the desktop environment, but will not bash the installation of OpenOffice 3.0

It wasn't an issue for me, since I always remove Ekiga anyway, which has the effect of removing the gnome-desktop-environment. Please note that the gnome-desktop-environment is a meta-package. The individual programs are still installed and still work together as required. I have been running for months - both in Hardy and lately in Ibex.

I haven't tested in Kubuntu, since I don't use it.

Hope this helps.

---

### Post by shane19174 on 2008-10-21
> I am using ubuntu 8.10 beta. I'm not sure if this works on Hardy, but after completing the installation according to my instructions,

Code:

sudo apt-get install gnome-desktop-environment

will restore the desktop environment, but will not bash the installation of OpenOffice 3.0

It wasn't an issue for me, since I always remove Ekiga anyway, which has the effect of removing the gnome-desktop-environment. Please note that the gnome-desktop-environment is a meta-package. The individual programs are still installed and still work together as required. I have been running for months - both in Hardy and lately in Ibex.

I haven't tested in Kubuntu, since I don't use it.

Hope this helps.

Sorry if I misunderstood something. In fact, I wasn't referring to your instructions, only noting the general conflict with removing OOo2.4, which I wouldn't recommend to someone without a deeper understanding of what's involved or at least a good set of instructions (like yours). Since I don't count myself among those with a deeper understanding of what's involved, I was glad to find calc's repo, which automated everything for me.

Anyway, like everyone else, I'm looking forward to a more permanent solution.

Shane

---

### Post by plun on 2008-10-21
> **shane19174 said:**
> OK, thanks for the clarification. I had noticed the yellow splash, but I didn't think anything of it. And I'm not working with any extensions at the moment. So I think I'll stick with calc's ppa until the backports are ready so I don't have to uninstall ubuntu-desktop.

Consensus for me is to skip Calcs ppa and install the real OO-3 final according to earlier manuals. (without removing)

OO-3 is also full of bugs...8-)  :)

Ubuntu-desktop is "untouched" and a little waste of space...

---

### Post by PinkFloyd102489 on 2008-10-21
I used these and it works fine.

```

# OpenOffice 3 Launchpad PPA
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

```

---

### Post by fballem on 2008-10-21
> **PinkFloyd102489 said:**
> I used these and it works fine.

```

# OpenOffice 3 Launchpad PPA
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

```

Have you tried to attach extensions? The reason I ask is that supplementary dictionaries (Canadian English and European Portuguese) are installed as extensions and I heard that the OpenOffice 3 in launchpad has a problem with extensions.

Like everyone else, I am hoping for a permanent solution very soon! There have been a lot of 'enthusiastic' discussions in the forums and in launchpad around support for OpenOffice 3.0 in Ibex. I gather that it will not be included in Ibex, but will be available in Backports. Don't know what the timing will be.

There are two reasons that I remove OpenOffice 2.4:

[LIST=1]
[*]I don't like running multiple versions of the same program on the same machine (that's a personal preference that has served me well for a lot of years).
[*]If you don't remove the old OpenOffice, then you cannot install the new OpenOffice as options on the Applications > Office menu - or at least not easily. These are installed through the instruction:```
sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb
```
[/LIST]

Hope this helps,

---

### Post by plun on 2008-10-21
> **fballem said:**
> 
Like everyone else, I am hoping for a permanent solution very soon! There have been a lot of 'enthusiastic' discussions in the forums and in launchpad around support for OpenOffice 3.0 in Ibex. I gather that it will not be included in Ibex, but will be available in Backports. Don't know what the timing will be.

There are two reasons that I remove OpenOffice 2.4:



Yes but it cannot be recommended for newbies.

I also noticed that Foresight Linux managed to include OO-3
[http://www.foresightlinux.org/releases/2-0-5.html](http://www.foresightlinux.org/releases/2-0-5.html)

A repo solution and a release note hint maybe ?

---

### Post by fballem on 2008-10-21
> **plun said:**
> Yes but it cannot be recommended for newbies.

I also noticed that Foresight Linux managed to include OO-3
[http://www.foresightlinux.org/releases/2-0-5.html](http://www.foresightlinux.org/releases/2-0-5.html)

A repo solution and a release note hint maybe ?

Been tried. Did mention that the discussions were 'enthusiastic' in both the forums and in launchpad!

Sometimes in my enthusiasm, I forget that I was a newbie not that long ago (only started on Linux/ubuntu in mid-May). Thanks for the gentle reminder.

Foresight uses a rolling release schedule, which will be a challenge for ubuntu, which uses a fixed six-month release schedule. I gather that there were some delays in releasing OpenOffice and the 'powers that be' did not feel that they could get OpenOffice sufficiently tested in time to make the Ibex release schedule. They also didn't want to slip the Ibex release schedule, since there are a number of other significant issues that are fixed in that release. It would have been nice, but ...

Intellectually, I understand the desire to continue with the release 'as is', but it would have been really nice if OpenOffice 3.0 were included. I also don't know if doing a point release (8.10.1) is an option, since the point releases are usually reserved for LTS releases, which 8.10 is not.

It is what it is, and hopefully the Backport will be ready soon for both Hardy and Ibex.

Regards,

---

### Post by yosumi on 2008-10-21
ok sorry to break your discussion but what's backport?

and since intrepid won't include ooo 3.0 beta (which i think is stupid. 2.4 is so obsolete), i should try foresight linux. it looks pretty interesting. 

and thanks for the detailed instructions on how to install ooo 3.0 beta. although it looks like alot of work, i'd definitely need it if i'm gonna stick with intrepid!

---

### Post by fballem on 2008-10-21
> **yosumi said:**
> ok sorry to break your discussion but what's backport?

and since intrepid won't include ooo 3.0 beta (which i think is stupid. 2.4 is so obsolete), i should try foresight linux. it looks pretty interesting. 

and thanks for the detailed instructions on how to install ooo 3.0 beta. although it looks like alot of work, i'd definitely need it if i'm gonna stick with intrepid!

Backports are contained in an additional repository for a release. It contains updated versions of programs that were not available on the release. They can be enabled through the Software Sources on System > Administration > Software Sources. I've attached a screenshot for your reference. Look at the last item of the Ubuntu updates.

As for the instructions to install OO3, if you open a terminal and keep the post open, then you can cut and paste from the post into Terminal. This takes a few minutes to do.

Regards,

---

### Post by thomas228 on 2008-10-21
> **fballem said:**
> To install Open Office 3.0 using software that is obtained from [http://www.openoffice.org](http://www.openoffice.org) directly, do the following:

- Uninstall the existing installation of Open Office 2.4 software (this is a really long command string - please make sure you get all of it):

```
sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer

```
- Change to the folder containing the download archive and extract the files from the archive:

```
cd ~/Desktop
tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
cd OOO300_m9_native_packed-1_en-US.9358/DEBS

```
- Install OpenOffice:

```
sudo dpkg -i *.deb
```

- Intall the OpenOffice menus. This can only be done if OpenOffice 2.4 was removed:

```
sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb

```

Hope this helps,

Very good installation instructions

If you mess up the installation order and have to uninstall 00o3 heres something from tomubuntu.com that may help
"Want to remove OpenOffice 3? I’ve compiled this huge command (it’s all one line) to remove all of the OpenOffice 3 packages:

sudo apt-get remove ooobasis3.0-base ooobasis3.0-binfilter ooobasis3.0-calc ooobasis3.0-core01 ooobasis3.0-core02 ooobasis3.0-core03 ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core06 ooobasis3.0-core07 ooobasis3.0-draw ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-binfilter ooobasis3.0-en-us-calc ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress ooobasis3.0-en-us-math ooobasis3.0-en-us-res ooobasis3.0-en-us-writer ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3 openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math openoffice.org3-writer openoffice.org-ure    "

I'm sticking with hardy for a while and have the full released installation of 00o3.
Works pretty good for me

Good luck
Tom

---

### Post by fballem on 2008-10-21
> **thomas228 said:**
> Very good installation instructions

If you mess up the installation order and have to uninstall 00o3 heres something from tomubuntu.com that may help
"Want to remove OpenOffice 3? I’ve compiled this huge command (it’s all one line) to remove all of the OpenOffice 3 packages:

sudo apt-get remove ooobasis3.0-base ooobasis3.0-binfilter ooobasis3.0-calc ooobasis3.0-core01 ooobasis3.0-core02 ooobasis3.0-core03 ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core06 ooobasis3.0-core07 ooobasis3.0-draw ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-binfilter ooobasis3.0-en-us-calc ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress ooobasis3.0-en-us-math ooobasis3.0-en-us-res ooobasis3.0-en-us-writer ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3 openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math openoffice.org3-writer openoffice.org-ure    "

I'm sticking with hardy for a while and have the full released installation of 00o3.
Works pretty good for me

Good luck
Tom

Curious to know if you lost the gnome-desktop-environment. If you did, then you might want to re-install it. You can do this through Synaptic or through
```
sudo apt-get install gnome-desktop-environment
```

Regards,

---

### Post by thomas228 on 2008-10-21
> **fballem said:**
> Curious to know if you lost the gnome-desktop-environment. If you did, then you might want to re-install it. You can do this through Synaptic or through
```
sudo apt-get install gnome-desktop-environment
```

Regards,

Got all seven apps in application>office using 00o3 tarball and following the terminal commands recommended See post #3 at http://ubuntuforums.org/showthread.php?t=953487
Thanks
When I ran the first app it gave  me the option of registering as well as an option for auto updates.

Not a bad set of programs Sure beats microsoft' office

Tom

---

