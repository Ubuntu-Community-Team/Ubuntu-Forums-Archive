---
title: "gzip: sfx_archive.tar.gz: not in gzip format ------intsall of thinkorswim"
date: 2018-06-23
forum: MINT
---

### Post by timmy96815 on 2018-06-23
[LIST]
[*]sudo apt-add-repository ppa:webupd8team/java
[*]sudo apt-get update
[*]sudo apt-get install oracle-java8-installer
[/LIST]

I typed all this into the terminal

then when I went to run the thinkorswim_installer.sh it gave me this error



jeff@jeff-To-be-filled-by-O-E-M ~/Downloads $ sh ./thinkorswim_installer.sh 

gzip: sfx_archive.tar.gz: not in gzip format

I am sorry, but the installer file seems to be corrupted.
If you downloaded that file please try it again. If you
transfer that file with ftp please make sure that you are
using binary mode.
jeff@jeff-To-be-filled-by-O-E-M ~/Downloads $ ./thinkorswim_installer.sh^C
jeff@jeff-To-be-filled-by-O-E-M ~/Downloads $ 


Here is the computer information

LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    LinuxMint
Description:    Linux Mint 17.1 Rebecca
Release:    17.1
Codename:    rebecca


Does anybody have any suggestions to get the options trading platform think or swim up and running? Thanks

---

### Post by deadflowr on 2018-06-24
*Thread moved to **MINT***

---

### Post by yancek on 2018-06-24
Did you try downloading again as suggested in the output from the command which indicates the download was corrupt?

---

### Post by timmy96815 on 2018-06-24
> **yancek said:**
> Did you try downloading again as suggested in the output from the command which indicates the download was corrupt?

I tried several times on two different computers. Icouldn't get it to work on either. I even installed the most current distro of ubuntu 18.02. Still no luck.
I also tried downloading the installer from the command prompt. No luck and same error. It is strange on both computers the same error.

---

### Post by spjackson on 2018-06-25
> **timmy96815 said:**
> I tried several times on two different computers. Icouldn't get it to work on either. I even installed the most current distro of ubuntu 18.02. Still no luck.
I also tried downloading the installer from the command prompt. No luck and same error. It is strange on both computers the same error.
If you downloaded this [https://mediaserver.thinkorswim.com/installer/InstFiles/thinkorswim_installer.sh](https://mediaserver.thinkorswim.com/installer/InstFiles/thinkorswim_installer.sh) then the problem is that it is currently broken; it doesn't matter how many computers you try it on, you will get the same error. You will need to ask the provider of the software to correct the fault, or wait until they correct it.

---

### Post by timmy96815 on 2018-06-25
> **spjackson said:**
> If you downloaded this [https://mediaserver.thinkorswim.com/installer/InstFiles/thinkorswim_installer.sh](https://mediaserver.thinkorswim.com/installer/InstFiles/thinkorswim_installer.sh) then the problem is that it is currently broken; it doesn't matter how many computers you try it on, you will get the same error. You will need to ask the provider of the software to correct the fault, or wait until they correct it.

Wow, that makes sense. I should have more confidence. I usually can get things up and running. I am going to message the provider. Thanks

---

### Post by ibcapitalmgt on 2018-07-05
I am having the same issues using Ubuntu 18. has anyone confirmed that it is indeed the file is bad? I have seen elsewhere that others aren't having this problem

---

### Post by ibcapitalmgt on 2018-07-06
As of yesterday, 7/5/18, according to a representative of TD Ameritrade they have resolved this issue for most Linux users. However, I am one who needed to be sent an older version for some reason and now I'm up and running. Meaning, the error is indeed due to an issue on thinkorswim technical side.
If you are still having issues, I can upload the file that I received, just ask

---

### Post by luis-feliu on 2018-07-07
> **ibcapitalmgt said:**
> As of yesterday, 7/5/18, according to a representative of TD Ameritrade they have resolved this issue for most Linux users. However, I am one who needed to be sent an older version for some reason and now I'm up and running. Meaning, the error is indeed due to an issue on thinkorswim technical side.
If you are still having issues, I can upload the file that I received, just ask

Could you please upload the installation script?  I'm having issues with the file hosted on the thinkorswim site. Thanks.

---

### Post by wolf4warren on 2018-07-09
> **ibcapitalmgt said:**
> As of yesterday, 7/5/18, according to a representative of TD Ameritrade they have resolved this issue for most Linux users. However, I am one who needed to be sent an older version for some reason and now I'm up and running. Meaning, the error is indeed due to an issue on thinkorswim technical side.
If you are still having issues, I can upload the file that I received, just ask

Please send me a link to the uploaded file.  I am having the same problem with Ubuntu 16.04 running ThinkorSwim since July 5th.

Thanks in advance,  Doug

---

### Post by jagan_indian9 on 2018-07-12
[COLOR=#000000]Please send me a link to the uploaded file. I am having the same problem with ThinkorSwim[/COLOR]

---

### Post by nvu on 2018-07-12
here it is: [https://we.tl/mDukQD1gCO](https://we.tl/mDukQD1gCO)

---

### Post by kacstereo on 2018-07-18
> **luis-feliu said:**
> Could you please upload the installation script?  I'm having issues with the file hosted on the thinkorswim site. Thanks.

Hello. I experience the same problem. If you can send me a copy of the script, thanks a lot for that too.

---

### Post by dpdesmond on 2018-07-22
I hit the same thing today. Wrote TDA and was told they "don't support" Linux despite the installer link and instructions still being all over the place on their website.

The installer tries to tail an archive with the goods out of the script file itself, but the offset it uses isn't an archive. There are pieces of a .tar.gz in there, but it's seemingly corrupt. The most recent version on web.archive from 2015:
[https://web.archive.org/web/20150806113249/https://mediaserver.thinkorswim.com/installer/InstFiles/thinkorswim_installer.sh](https://web.archive.org/web/20150806113249/https://mediaserver.thinkorswim.com/installer/InstFiles/thinkorswim_installer.sh)

 ... manages to run and install, but now "Installing updates..." spins for ~10 minutes at a time and complains about internet connectivity.

Next, took my updated ToS install from Mac and copied the thinkorswim/thinkorswim bootstrapper script from the 2015 linux version into it. Same thing, runs but no internet connectivity. Maybe JRE needs to be given network access somehow? Beats me.

Gave up and installed the Windows version with Wine. It seems to run as well as I'd have expected the "native" version to.

[ATTACH=CONFIG]280478[/ATTACH]

---

### Post by rhcpng on 2018-08-06
Did you install the 32 or 64 bit version in Wine? I tried installing it on Linux Mint, but it's stuck at "Downloading updates" when I run TOS.

---

### Post by tornado4242 on 2018-09-06
i am running linux MINT.

i used this thread to update to java version 1.8****
[https://ubuntuforums.org/showthread.php?t=2311233](https://ubuntuforums.org/showthread.php?t=2311233)


use the link and wget the download
[https://web.archive.org/web/20150806...m_installer.sh]("https://web.archive.org/web/20150806113249/https://mediaserver.thinkorswim.com/installer/InstFiles/thinkorswim_installer.sh")

run
sudo sh ./thinkorswim_installer.sh

it does cycle through several updates but it will run after about 25 mins or so.

---

### Post by ramirez.cervantes on 2018-09-25
Hello, could you please share the file? I'm having the same problem. My email is [email]ramirez.cervantes@gmail.com[/email] Thanks.

---

