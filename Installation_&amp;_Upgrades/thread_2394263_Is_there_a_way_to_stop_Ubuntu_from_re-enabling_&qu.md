---
title: "Is there a way to stop Ubuntu from re-enabling &quot;deb cdrom&quot; even if I have already dis"
date: 2018-06-14
forum: Installation &amp; Upgrades
---

### Post by Gustavo_Benedito_d on 2018-06-14
Hello,

I found it too annoying. I always have disabled "deb cdrom" in both Software Update and in /etc/apt/sources.list. But when every time I update, Ubuntu re-enables "deb cdrom", causing error in the terminal, then I have to disable, comment or remove it for getting rid of the error and updating without errors. But the next time, update or in the future Ubuntu will re-enable and keep re-enabling "deb cdrom". Ubuntu re-enabling it is like it is a time-travelling sorecerer. 

Do you know some trick or way to stop or prevent Ubuntu from re-enabling "deb cdrom" in the next updates?

Thank you for your attention and help!

---

### Post by QIII on 2018-06-14
Are you saying you comment out 

```
deb cdrom:
```

in /etc/apt/sources.list so that it looks like

```
# deb cdrom:
```

and it later appears again as

```
deb cdrom:
```?

Would you please post the content of /etc/apt/sources.list?

---

### Post by Gustavo_Benedito_d on 2018-06-14
Sorry, I have just corrected my post to clear confusion.

I meant I commented to get rid of "deb cdrom", but Ubuntu uncommented again. 

For this reason, see the result:

```
[COLOR=#333333][FONT=Ubuntu]Ign:1 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic InRelease
Err:2 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic Release
  Please use apt-cdrom to allow APT to recognise this CD-ROM. 'apt-get update' cannot be used to add new CD-ROMs[/FONT][/COLOR]
```

Here is the [FONT=courier new]/etc/apt/sources.list[/FONT]:

```
[COLOR=#EBCB8B]deb[/COLOR][COLOR=#A3BE8C]** cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/**[/COLOR][COLOR=#BF616A]** bionic**[/COLOR][COLOR=#B48EAD]** main restricted**[/COLOR]
[COLOR=#EBCB8B]deb[/COLOR][COLOR=#A3BE8C]** [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)**[/COLOR][COLOR=#BF616A]** bionic**[/COLOR][COLOR=#B48EAD]** partner**[/COLOR]
[COLOR=#EBCB8B]deb[/COLOR][COLOR=#A3BE8C]** [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)**[/COLOR][COLOR=#BF616A]** bionic**[/COLOR][COLOR=#B48EAD]** main universe restricted multiverse**[/COLOR]
[COLOR=#EBCB8B]deb[/COLOR][COLOR=#A3BE8C]** [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)**[/COLOR][COLOR=#BF616A]** bionic-backports**[/COLOR][COLOR=#B48EAD]** universe restricted main multiverse**[/COLOR]
[COLOR=#EBCB8B]deb[/COLOR][COLOR=#A3BE8C]** [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)**[/COLOR][COLOR=#BF616A]** bionic-proposed**[/COLOR][COLOR=#B48EAD]** universe restricted multiverse main**[/COLOR]
[COLOR=#EBCB8B]deb[/COLOR][COLOR=#A3BE8C]** [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)**[/COLOR][COLOR=#BF616A]** bionic-updates**[/COLOR][COLOR=#B48EAD]** universe restricted main multiverse**[/COLOR]
[COLOR=#EBCB8B]deb[/COLOR][COLOR=#A3BE8C]** [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)**[/COLOR][COLOR=#BF616A]** bionic-security**[/COLOR][COLOR=#B48EAD]** universe restricted main multiverse**[/COLOR]
[COLOR=#EBCB8B]deb-src[/COLOR][COLOR=#A3BE8C]** [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)**[/COLOR][COLOR=#BF616A]** bionic**[/COLOR][COLOR=#B48EAD]** partner**[/COLOR]
[COLOR=#EBCB8B]deb-src[/COLOR][COLOR=#A3BE8C]** [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)**[/COLOR][COLOR=#BF616A]** bionic**[/COLOR][COLOR=#B48EAD]** main restricted **[/COLOR][COLOR=#81A1C1]**#Added by software-properties**[/COLOR]
[COLOR=#EBCB8B]deb-src[/COLOR][COLOR=#A3BE8C]** [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)**[/COLOR][COLOR=#BF616A]** bionic**[/COLOR][COLOR=#B48EAD]** main universe restricted multiverse **[/COLOR][COLOR=#81A1C1]**#Added by software-properties**[/COLOR]
[COLOR=#EBCB8B]deb-src[/COLOR][COLOR=#A3BE8C]** [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)**[/COLOR][COLOR=#BF616A]** bionic-updates**[/COLOR][COLOR=#B48EAD]** universe restricted main multiverse **[/COLOR][COLOR=#81A1C1]**#Added by software-properties**[/COLOR]
[COLOR=#EBCB8B]deb-src[/COLOR][COLOR=#A3BE8C]** [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)**[/COLOR][COLOR=#BF616A]** bionic-security**[/COLOR][COLOR=#B48EAD]** universe restricted main multiverse **[/COLOR][COLOR=#81A1C1]**#Added by software-properties**[/COLOR]
```

Every time I update, Ubuntu uncomments and I have to comment to remove the error. But Ubuntu will uncomment again next time before I update. It is like as if a time-travelling sorcerer trapped me in the infinitve lopp, I redo and he undoes.

---

### Post by deadflowr on 2018-06-14
How are you editing your sources.list?
Show the command or other method you use.

---

### Post by Gustavo_Benedito_d on 2018-06-14
I use nano and Gedit and I changed like:

```
# deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic main universe restricted multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic-backports universe restricted main multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic-proposed universe restricted multiverse main
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic-updates universe restricted main multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security universe restricted main multiverse
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main restricted #Added by software-properties
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic main universe restricted multiverse #Added by software-properties
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic-updates universe restricted main multiverse #Added by software-properties
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security universe restricted main multiverse #Added by software-properties
```

In the next times and updates, Ubuntu will uncomment and also will duplicate or multiplicate the "deb cdrom":

```
deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted
deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted
deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic main universe restricted multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic-backports universe restricted main multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic-proposed universe restricted multiverse main
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic-updates universe restricted main multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security universe restricted main multiverse
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main restricted #Added by software-properties
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic main universe restricted multiverse #Added by software-properties
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic-updates universe restricted main multiverse #Added by software-properties
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security universe restricted main multiverse #Added by software-properties
```

---

### Post by QIII on 2018-06-14
deadflowr asked if you would please post the exact command you used to affect the changes.

Would you please edit your /etc/apt/sources.list, then update & dist-upgrade from the terminal rather than using a GUI package manager and let us know what happens?

---

### Post by Gustavo_Benedito_d on 2018-06-15
I am trying to clarify and simplify my situation and what happened.

1. I used the command like:

```
sudo apt update
```

2. Then I got an error:

```
Ign:1 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic InReleaseErr:2 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic Release
  Please use apt-cdrom to allow APT to recognise this CD-ROM. 'apt-get update' cannot be used to add new CD-ROMs
```

[FONT=arial]3. I noticed Ubuntu uncommented. I solved the following command:[/FONT]

```
sudo nano /etc/apt/sources.list
```

[FONT=arial]4. I commented "deb cdrom"[/FONT]

```
# deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic$
```
[FONT=arial]Or I removed this line.

5. I commanded again:[/FONT]

```
sudo apt update
```

[FONT=arial]6. Here is the result:[/FONT]

```
sudo apt update
Hit:1 http://ppa.launchpad.net/gusbemacbe/ppa/ubuntu bionic InRelease
Hit:2 http://apt.insynchq.com/ubuntu bionic InRelease                          
Hit:3 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Hit:4 http://archive.canonical.com/ubuntu bionic InRelease                     
Hit:5 http://gb.archive.ubuntu.com/ubuntu bionic InRelease                     
Hit:6 http://archive.ubuntu.com/ubuntu bionic InRelease                        
Hit:7 https://packages.microsoft.com/repos/vscode stable InRelease             
Hit:8 http://ppa.launchpad.net/numix/ppa/ubuntu bionic InRelease               
Hit:9 https://download.sublimetext.com apt/dev/ InRelease                      
Hit:10 http://gb.archive.ubuntu.com/ubuntu bionic-backports InRelease          
Hit:12 http://gb.archive.ubuntu.com/ubuntu bionic-proposed InRelease           
Hit:13 http://ppa.launchpad.net/webupd8team/brackets/ubuntu bionic InRelease   
Hit:14 http://gb.archive.ubuntu.com/ubuntu bionic-updates InRelease            
Hit:11 https://packages.gitlab.com/gitlab/gitlab-ee/ubuntu bionic InRelease    
Hit:16 https://packages.gitlab.com/runner/gitlab-runner/ubuntu bionic InRelease
Hit:15 https://packagecloud.io/AtomEditor/atom/any any InRelease               
Reading package lists... Done 
Building dependency tree       
Reading state information... Done
9 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

[FONT=arial]The error is gone. Perfectly.

6. But... **the next time**, Ubuntu **will undo**... I will run the same command:[/FONT]

```
sudo apt update
```

[FONT=arial]The same error appears again because Ubuntu uncommented before I update. 

[/FONT]```
Ign:1 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic InReleaseErr:2 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic Release
  Please use apt-cdrom to allow APT to recognise this CD-ROM. 'apt-get update' cannot be used to add new CD-ROMs
```[FONT=arial]

I and Ubuntu repeat the same things. I am trapped in the infinite loop of commenting, uncommenting and same error. 

I also did via Software Update and Ubuntu also undid. I remember I ran Software Update as sudo. [/FONT][FONT=arial]
[/FONT]
[FONT=arial]Did you understand? Was it clear?[/FONT]

---

### Post by QIII on 2018-06-15
I can't reproduce this.

How did you install Ubuntu?  Is it on a hard drive, USB drive, persistent USB drive?

---

### Post by Gustavo_Benedito_d on 2018-06-15
It is a persistent USB drive.

I installed persistent Ubuntu on an external HD via mkusb, from a CD-ROM of Ubuntu, extracting the ISO of Ubuntu from a USB drive.

---

### Post by QIII on 2018-06-15
I would have to do some research (and it's late here) but I am not sure that you can change system files on a persistent USB install.  I'm not sure the persistent overlay plays that way with system files.  You can install packages, update, save files, change user preferences and such.  But I think a change to a system file would persist only as long as it resides in memory.  So you might get one update done while you have a terminal session, but you'd lose it when you closed the session and be back to the original.

Seems a bit silly since people use persistent USBs all the time, so I may be way off base.

I have to sleep now and I'll be working at a client's office all day tomorrow, but I might be able to experiment with that tomorrow evening -- say 16 or 18 hours from now.

---

### Post by Gustavo_Benedito_d on 2018-06-15
HI QII,

Because I use persistent OS for college, so I have different two computers and my class has a lot of different computers. Therefore, persistent OS is designed for working on any computers, independently of OS, without depending on CPU, GPU, etc.

---

### Post by QIII on 2018-06-15
I am well aware of what a persistent USB installation is.  That's exactly why I'm wondering about whether changes to system configuration files would be saved between sessions.

---

