---
title: "Install Code Blocks"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by neonl on 2007-09-23
Hi.

I heard about code blocks as great programing suite for C/C++ and want to give it a try.

How do I install the packages in Ubuntu Festy?

Thanks

---

### Post by Pumalite on 2007-09-23
[http://sourceforge.net/projects/codeblocks](http://sourceforge.net/projects/codeblocks)

---

### Post by Rui Pais on 2007-09-25
> **Pumalite said:**
> [http://sourceforge.net/projects/codeblocks](http://sourceforge.net/projects/codeblocks)

hi, in the case of code::blocks, the latest svn is a better suggestion then the old "stable", that is too obsolete (2005).

[Here a link for the nightly  build]("http://forums.codeblocks.org/index.php?PHPSESSID=c200b830677bb94ff3ce3fa284e56c43&board=20.0"), there are binaries versions for all Ubuntu flavors.

There are too, on Code::Blocks wiki ([here]("http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks#Alternative_method_for_installing_a_nightly_build")), instructions to compile from source
(with some specific topic on Ubuntu).

---

### Post by neonl on 2007-09-25
> **Rui Pais said:**
> hi, in the case of code::blocks, the latest svn is a better suggestion then the old "stable", that is too obsolete (2005).

[Here a link for the nightly  build]("http://forums.codeblocks.org/index.php?PHPSESSID=c200b830677bb94ff3ce3fa284e56c43&board=20.0"), there are binaries versions for all Ubuntu flavors.

There are too, on Code::Blocks wiki, instructions to compile from source
(with some specific topic on Ubuntu).

Ok, I'll give it a try, by the way (offtopic), usplash alive and kicking.

---

### Post by Rui Pais on 2007-09-25
> **neonl said:**
> ... (offtopic), usplash alive and kicking.

nice to hear that :)

---

### Post by neonl on 2007-12-05
> **Rui Pais said:**
> hi, in the case of code::blocks, the latest svn is a better suggestion then the old "stable", that is too obsolete (2005).

[Here a link for the nightly  build]("http://forums.codeblocks.org/index.php?PHPSESSID=c200b830677bb94ff3ce3fa284e56c43&board=20.0"), there are binaries versions for all Ubuntu flavors.

There are too, on Code::Blocks wiki ([here]("http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks#Alternative_method_for_installing_a_nightly_build")), instructions to compile from source
(with some specific topic on Ubuntu).

Hi Rui.

Can you tell me how to find the Ubuntu/Linux version? Every time I open one of those topics it's written "Windows <version> | Linux -> none"...

Regards

---

### Post by cstudent on 2007-12-05
> **neonl said:**
> Hi Rui.

Can you tell me how to find the Ubuntu/Linux version? Every time I open one of those topics it's written "Windows <version> | Linux -> none"...

Regards

Check again here: [http://forums.codeblocks.org/index.php/topic,7402.0.html](http://forums.codeblocks.org/index.php/topic,7402.0.html)

Read second post.

---

### Post by neonl on 2007-12-05
> **cstudent said:**
> Check again here: [http://forums.codeblocks.org/index.php/topic,7402.0.html](http://forums.codeblocks.org/index.php/topic,7402.0.html)

Read second post.

Thank you very much. I'm installing for those french repositories mentioned in the topic. I presume it will update with APT, am I right?

---

### Post by cstudent on 2007-12-06
> **neonl said:**
> Thank you very much. I'm installing for those french repositories mentioned in the topic. I presume it will update with APT, am I right?

If you use one of the repositories, yes it will update. You may end up turning the repo off. When the developers get on a roll, you may get an update everyday. It might get annoying. :)

---

### Post by Rui Pais on 2007-12-06
Glad you find a solution, neonl,
sorry i'm been very busy here and i miss your question.
Luckily cstudent saw your question :)

see you,
Rui.

---

### Post by wizardofyendor on 2007-12-06
add these repositories:

```

deb http://lgp203.free.fr/ubuntu/ distname1 universe
deb http://apt.wxwidgets.org/ distname2 main

```

replace distname1 with either gutsy, feisty, or edgy.
replace distname2 with either gutsy-wx, feisty-wx, or edgy-wx.

get the gpg key for the repos:

```

wget -q http://lgp203.free.fr/public.key -O- | sudo apt-key add -
wget -q http://apt.wxwidgets.org/key.asc -O- | sudo apt-key add -

```

and to install the nightly build of code::blocks use:
```
sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
```

This will keep you updated thru update-manager with the newest nightly build.

---

### Post by neonl on 2007-12-06
> **cstudent said:**
> If you use one of the repositories, yes it will update. You may end up turning the repo off. When the developers get on a roll, you may get an update everyday. It might get annoying. :)

Yeah, It's annoying that it updates every day, especially because the repo is sloooooooww :).

> **Rui Pais said:**
> Glad you find a solution, neonl,
sorry i'm been very busy here and i miss your question.
Luckily cstudent saw your question :)

see you,
Rui.

No problem, Rui. These are the advantages of a huge community.

You have been a great help in my swapping to Linux (Ubuntu).

Cya ;)

---

### Post by RudolfMDLT on 2008-01-10
> **wizardofyendor said:**
> add these repositories:

```

deb http://lgp203.free.fr/ubuntu/ distname1 universe
deb http://apt.wxwidgets.org/ distname2 main

```

replace distname1 with either gutsy, feisty, or edgy.
replace distname2 with either gutsy-wx, feisty-wx, or edgy-wx.

get the gpg key for the repos:

```

wget -q http://lgp203.free.fr/public.key -O- | sudo apt-key add -
wget -q http://apt.wxwidgets.org/key.asc -O- | sudo apt-key add -

```

and to install the nightly build of code::blocks use:
```
sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
```

This will keep you updated thru update-manager with the newest nightly build.

I have followed this and the HowTo in the CodeBlocks Wiki but I keep getting this error when doing an apt-update:

> Hit [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty/all Packages                
Err [http://apt.wxwidgets.org](http://apt.wxwidgets.org) gusty/main Packages
  404 Not Found
Ign [http://lgp203.free.fr](http://lgp203.free.fr) gusty Release.gpg    
Ign [http://lgp203.free.fr](http://lgp203.free.fr) gusty/universe Translation-en_ZA                     
Ign [http://lgp203.free.fr](http://lgp203.free.fr) gusty Release                                        
Ign [http://lgp203.free.fr](http://lgp203.free.fr) gusty/universe Packages                              
Err [http://lgp203.free.fr](http://lgp203.free.fr) gusty/universe Packages 
  404 Not Found
Fetched 12.3kB in 15s (815B/s)
Failed to fetch [http://apt.wxwidgets.org/dists/gusty/main/binary-i386/Packages.gz](http://apt.wxwidgets.org/dists/gusty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://lgp203.free.fr/ubuntu/dists/gusty/universe/binary-i386/Packages.gz](http://lgp203.free.fr/ubuntu/dists/gusty/universe/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


and then because of that I assume:

> rudolf@Rudolf:~$ sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcodeblocks0
rudolf@Rudolf:~$ 


Please help get this right! It can't be so hard to install something!

Thanks,

Rudolf

---

### Post by ljp37 on 2008-01-10
The problem is
[INDENT][I]deb [http://lgp203.free.fr/ubuntu/](http://lgp203.free.fr/ubuntu/) distname1 universe
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) distname2 main[/I]
[/INDENT]
For gutsy, these should read
[INDENT]
deb [http://lgp203.free.fr/ubuntu/](http://lgp203.free.fr/ubuntu/) gutsy universe
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main[/INDENT]

---

### Post by biasedopiniondrummer on 2008-02-06
Hey guys, i have double checked my repository list and i am still getting this error when I try to install Code::Blocks

clay@clay-laptop:~$ sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcodeblocks0


What can I do to fix this?

Thanks
Clay

---

### Post by biasedopiniondrummer on 2008-02-06
AH! i just fixed my problem. thanks!

---

### Post by BCCISProf on 2008-02-20
Could you enlighten me as to how you fixed it. I am having the same problem.

Thanks

---

### Post by Fonzy on 2008-02-29
> **BCCISProf said:**
> Could you enlighten me as to how you fixed it. I am having the same problem.

Thanks

```
apt-get update
```

After that apt should find libcodeblocks0 if you try to install it. :)

---

### Post by ggunited on 2008-03-09
Hi guys,

I had the same problems as you and I finally installed it as it is indicated.
Thanks for the method

---

### Post by MPetrosino on 2008-03-11
Im very new to linux so i dont know what the first thing to do is. I downloaded the code::blocks 32-bit application. Next I extracted everything on my desktop. IDK how to install new repositories. whenever i try the code given

```
root@viki:/home/mpetrosino# deb http://lgp203.free.fr/ubuntu/gutsy universe
bash: deb: command not found

```

so now do i have to install the 'deb' command, then install everything else??? Im really lost.

---

### Post by Rui Pais on 2008-03-11
> **MPetrosino said:**
> Im very new to linux so i dont know what the first thing to do is. I downloaded the code::blocks 32-bit application. Next I extracted everything on my desktop. IDK how to install new repositories. whenever i try the code given

```
root@viki:/home/mpetrosino# deb http://lgp203.free.fr/ubuntu/gutsy universe
bash: deb: command not found

```

so now do i have to install the 'deb' command, then install everything else??? Im really lost.

No, you must add those lines to your sources.list, not enter it as command.
Just type on a terminal:
```
sudo sh -c "echo 'deb http://lgp203.free.fr/ubuntu/gutsy universe' >> /etc/apt/sources.list"
sudo sh -c "echo 'deb http://apt.wxwidgets.org/ gutsy-wx main' >> /etc/apt/sources.list"

```
then:
```
sudo apt-get update
```
and when it finishs:
```
sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
```
:)

---

### Post by MPetrosino on 2008-03-11
I entered in everything exactly how you told me... Here is everything exactly out of terminal.

```
root@viki:/home/mpetrosino# sudo sh -c "echo 'deb http://lgp203.free.fr/ubuntu/gutsy universe' >> /etc/apt/sources.list"

root@viki:/home/mpetrosino# sudo sh -c "echo 'deb http://apt.wxwidgets.org/ gutsy-wx main' >> /etc/apt/sources.list"

root@viki:/home/mpetrosino# sudo apt-get update
E: Malformed line 2 in source list /etc/apt/sources.list (dist parse)

root@viki:/home/mpetrosino# sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
E: Malformed line 2 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

```

---

### Post by Rui Pais on 2008-03-12
Can you post the output of 
```
cat /etc/apt/sources.list
```
please?

---

### Post by MPetrosino on 2008-03-12
```
mpetrosino@viki:~$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse restricted universe main
deb http://lgp203.free.fr/ubuntu/gutsy universe
deb http://apt.wxwidgets.org/ gutsy-wx main
mpetrosino@viki:~$ 

```

---

### Post by Rui Pais on 2008-03-12
> **MPetrosino said:**
> ```
mpetrosino@viki:~$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse restricted universe main
deb http://lgp203.free.fr/ubuntu/gutsy universe
deb http://apt.wxwidgets.org/ gutsy-wx main
mpetrosino@viki:~$ 

```

Ah ok. 
I made the command lines from your post commands, that contained a typo, without checking ... :(

You must edit your sources file:
```
gksudo gedit /etc/apt/sources.list
```

and change 2nd line:
```
deb http://lgp203.free.fr/ubuntu**/g**utsy universe
```
to
```
deb http://lgp203.free.fr/ubuntu/ gutsy universe
```
Thats a space between "ubuntu/" and "gutsy".
After that it should work.

---

### Post by MPetrosino on 2008-03-13
ok everything you helped me with worked out perfectly but i do still have one problem 
heres the code:

```
root@viki:/home/mpetrosino# sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcodeblocks0: Depends: libwxgtk2.8-0 (>= 2.8.7) but it is not going to be installed
E: Broken packages
root@viki:/home/mpetrosino#
```

---

### Post by Rui Pais on 2008-03-13
Well it seems to have a broken package.

You can try to locate which one it is by opening synaptic, and go:
Custom Filters *(bottom left)* > Broken *(top left)*
If it list any broken package double click on it to fix it.
If not try on aterminal:
```
sudo apt-get install -f
```

hth

---

### Post by MPetrosino on 2008-03-13
Ok i checked the synaptic package manager like you told me and there were no broken packages so i went to terminal and heres the results:

```
root@viki:/home/mpetrosino# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@viki:/home/mpetrosino# 
```

it appears nothing was updated.....so now im at (yet again) another roadblock.

---

### Post by Rui Pais on 2008-03-14
> **MPetrosino said:**
> Ok i checked the synaptic package manager like you told me and there were no broken packages so i went to terminal and heres the results:

```
root@viki:/home/mpetrosino# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@viki:/home/mpetrosino# 
```

it appears nothing was updated.....so now im at (yet again) another roadblock.

Thats strange. Well at least you don't seems to have nothing really broken on your system... 

Try to narrow down the possible killer. Install first the needed dependencies:
```
sudo apt-get install libwxgtk2.8-0 libwxgtk2.8-dev wx2.8-headers wx-common
```
then try again:
```
sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
```
if that fails you can try to manually download deb packages and install one by one to see if you can make it or found more info on which is failing.

good luck, and don't forget to post the error output if some step fails.

---

### Post by MPetrosino on 2008-04-14
i couldnt figure out how to delete so look at my next post....sorry.

---

### Post by MPetrosino on 2008-04-14
ok so heres the code and results:

```

mpetrosino@viki:~$ sudo apt-get install libwxgtk2.8-0 libwxgtk2.8-dev wx2.8-headers wx-common
[sudo] password for mpetrosino:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwxgtk2.8-0: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
E: Broken packages

```

and for the second part:
```

mpetrosino@viki:~$ sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcodeblocks0: Depends: libwxgtk2.8-0 (>= 2.8.7) but it is not going to be installed
E: Broken packages
mpetrosino@viki:~$ 


```

---

### Post by pasgui on 2008-04-22
Hi,

Try to install the  [wxWidgets repository]("http://wiki.wxpython.org/InstallingOnUbuntuOrDebian")

Regards, pasgui

---

### Post by myle on 2008-04-25
> **wizardofyendor said:**
> add these repositories:

```

deb http://lgp203.free.fr/ubuntu/ distname1 universe
deb http://apt.wxwidgets.org/ distname2 main

```

replace distname1 with either gutsy, feisty, or edgy.
replace distname2 with either gutsy-wx, feisty-wx, or edgy-wx.

get the gpg key for the repos:

```

wget -q http://lgp203.free.fr/public.key -O- | sudo apt-key add -
wget -q http://apt.wxwidgets.org/key.asc -O- | sudo apt-key add -

```

and to install the nightly build of code::blocks use:
```
sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
```

This will keep you updated thru update-manager with the newest nightly build.

It works fine in Hardy, also.

---

### Post by lqvinh on 2008-05-02
Hi,
I did exactly like you said but I still got this error:

virtualdragon@ubuntu2:~$ sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcodeblocks0: Depends: libwxgtk2.8-0 (>= 2.8.7) but 2.8.6.1-0 is to be installed
E: Broken packages

As I can see this error occurs because my libwxgtk2.8 version is 2.8.6.1 but libcodeblocks0 requires version >=2.8.7. So how can I fix this? Please show me the way, I've tried many ways but it just keeps going wrong.

---

### Post by n3mes15 on 2008-05-22
It is important to execute 

```
sudo apt-get update
```

and 

```
sudo apt-get dist-upgrade
```

before trying to download the packages to have everything up-to-date.

---

