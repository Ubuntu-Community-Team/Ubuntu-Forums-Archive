---
title: "language support problems, Fix broken packages first."
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by hihihi100 on 2010-03-27
Everytime I click on system-administration-language support I get the following message:

```
The language support is not installed completely

Some translations or writing aids available for your chosen languages are not installed yet. Do you want to install them now?
```

If I click on install now, I get:

```
Could not apply changes!
Fix broken packages first.
```

I have tried via synaptic, to fix broken packages, but nothing happens, and I have also tried via terminal:

```
sudo apt-get install --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

I just executed those commands cause I found them in another thread...

Help please

Regards

Plus, everytime in this same application I choose  "for menus and windows" a language, and a different one for "startup and login" it automatically makes both options the same one, why?

---

### Post by stlsaint on 2010-03-27
look in synaptic package manager for the specific language pack you want and choose to install it from there. If it does not install than try using the fix packages command again and try to force install it using the -f switch:
```
sudo apt-get install -f <package>
```

---

### Post by hihihi100 on 2010-03-28
Now I only have to remember the name of that broken package... it only appeared when the system showed a red alarm icon on the upper pannel (it has something to do with spanish localized in argentina.

Can you suggest me any way of making the system show that problematic package?

cheers

---

### Post by Mart_L on 2010-03-31
Hi there,
the same thing is happening to me, just did the upgrade to Karmic, and now I can't finish the language support installation as described above.
Nonetheless I have no idea as to which are the possible broken packages, how do I find them?

Also in Wine when using Endnote, I have problems recognising the spanish symbols and characters, that is, I can write them but they aren't saved as such,(see the image attached), could this have sth to do with the language support problem?

Thanks

---

### Post by Angus77 on 2010-04-24
I don&t know why, but I have this problem now, too, as of today.  My Japanese 106-key keyboard layout diasappeared, and I have no idea what caused it.  Now I have a wonky keyboard, no Japanese input, and I can&t update my Language Support.

---

### Post by hihihi100 on 2010-04-25
this is the whole message that appears, in case it can be useful

```
E: /var/cache/apt/archives/gnome-user-guide-gu_2.28.0+git20090921ubuntu2_all.deb: trying to overwrite '/usr/share/omf/gnome-access-guide/gnome-access-guide-ar.omf', which is also in package gnome-user-guide-ar 0  
 E: /var/cache/apt/archives/kde-l10n-sr-latin_4%3a4.2.96-0ubuntu1_all.deb: trying to overwrite '/usr/share/locale/sr@latin/entry.desktop', which is also in package kde-l10n-sr 4
```so thats for arabic and serbian written in latin, no spanish... I apologise

---

### Post by michwe on 2010-05-04
It seems that Ubuntu is missing language files for the chosen user language and the english language. It solved the problem with the installation of each package manually. So type 'sudo synaptic' or open the *package manage*r in your Gnome menu. Install the packages mentioned after the start of language support.
(choose *language support* and click on *details* as soon as the message comes up). 

As I am German, I had to install the following packages. Finally it depends on your installation.

thunderbird-locale-en-gb
gimp-help-en
gnome-user-guide-en
openoffice.org-help-en-gb
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
openoffice.org-hyphenation
openoffice.org-hyphenation-en-us
openoffice.org-thesaurus-en-au
openoffice.org-thesaurus-en-us
language-pack-de
openoffice.org-help-de
thunderbird-locale-de
openoffice.org-l10n-de
language-pack-gnome-de
gimp-help-de
enigmail-locale-de
gnome-user-guide-de
language-support-writing-de
language-pack-de
openoffice.org-hyphenation-de
openoffice.org-thesaurus-de
openoffice.org-thesaurus-de-ch

---

### Post by srinivas1049 on 2010-05-16
Please help i am getting this error while trying upgrade it is saying there are some broken packages, i tried to fix them through installing 
sudo apt-get -f dist-upgrade


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  qemu-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/29.9kB of archives.
After this operation, 246kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 207541 files and directories currently installed.)
Unpacking qemu-common (from .../qemu-common_0.12.3+noroms-0ubuntu9_all.deb) ...
dpkg: error processing /var/cache/apt/archives/qemu-common_0.12.3+noroms-0ubuntu9_all.deb (--unpack):
 trying to overwrite '/etc/qemu-ifup', which is also in package qemu 0:0.12.3+noroms-0ubuntu9
Errors were encountered while processing:
 /var/cache/apt/archives/qemu-common_0.12.3+noroms-0ubuntu9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I tried to do it like


sudo apt-get clean
sudo apt-get update

but nothing positive 

i don't know what to do help me............

---

### Post by khughitt on 2010-08-24
Same problem here. Anyone figure out what the problem is?

---

### Post by nicknefarious on 2010-08-29
I think this is the same issue as this thread here... it may not help you solve your problem (or it may) but nice to keep it linked in some way so if anyone solves it we can all benefit.

[http://ubuntuforums.org/showthread.php?t=1445123]("http://ubuntuforums.org/showthread.php?t=1445123")

Check it out if interested.

Nick

---

### Post by khughitt on 2010-08-30
Thanks for the suggestion. Still no luck here, but it looks like it has been fixed in later versions:

[https://bugs.edge.launchpad.net/ubuntu/+source/language-selector/+bug/588254](https://bugs.edge.launchpad.net/ubuntu/+source/language-selector/+bug/588254)

Probably will have to wait for 10.10.

---

### Post by rykel on 2010-09-05
I am using Lucid with the latest updates, and yet I am also facing this exact same problem!

---

### Post by rykel on 2010-09-06
I found the solution. I had an OpenOffice PPA and the Ubuntu Language packages are unable to work with it. I removed the PPA and solved the problem already.     ):P

---

### Post by Costas100 on 2011-06-26
I have the same problem today on a fresh install of Ubuntu 10.04.2 LTS and I have no PPA repositories yet
The strange thing is when I checked in an older installation of Edubuntu 10.04 LTS (has been around for over a year now) I have the same problem, which appears when I tried to add a second language.

Costas

---

### Post by trainrabbit on 2011-09-16
Same here.....
But in my freshly installation i did find that kind of problem.
hopw somebody could fix this problem soon.
Regards.

---

### Post by trainrabbit on 2011-09-16
Sorry....my english not so good.
I just fix the problem on my computer...hope this can help
1. I open Update Manager then install update (if u cant find any update click setting on update manager then check "Important security update" and Recommended update").
2. When the update finish it will asking for restart, click "restart now".
after that u can open the "Languange Support" and do the update or install the language u want.
Good luck.. ;)

---

### Post by AlexDudko on 2011-09-16
> **trainrabbit said:**
> Same here.....
But in my freshly installation i did find that kind of problem.
hopw somebody could fix this problem soon.
Regards.

Just skip uninstallable packages and configure your language settings manually editing 
> /etc/default/locale

---

