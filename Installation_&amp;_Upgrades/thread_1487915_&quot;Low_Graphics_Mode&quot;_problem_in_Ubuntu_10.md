---
title: "&quot;Low Graphics Mode&quot; problem in Ubuntu 10.04 after update"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by krishnandu.sarkar on 2010-05-19
Hey friends, after I updated my ubuntu and restarted I get new boot menu

[http://img684.imageshack.us/i/image0008x.jpg/](http://img684.imageshack.us/i/image0008x.jpg/)

I went on with the first one as it is the updated version which I did recently. I faced "Low Graphics Mode" Problem. After that I thought there might be some problem with the new one but I face this problem with the existing one too.

Here is a screenshot of what I get after selecting the 1st or 3rd one.

[http://img208.imageshack.us/i/image0009s.jpg/](http://img208.imageshack.us/i/image0009s.jpg/)

After pressing OK, I see this...

[http://img17.imageshack.us/i/image0010d.jpg/](http://img17.imageshack.us/i/image0010d.jpg/)

Now after this screen no matter what I do I don't the GUI. I've tried all the options there.

The first and last option takes me to this screen [http://img576.imageshack.us/i/image0012p.jpg/](http://img576.imageshack.us/i/image0012p.jpg/) and keeps loading with no result.

Later from Windows I tried searching for the problem and get some solution in ubuntu forum...

```
starx
```

After running this command I saw initialization of GUI in KDE but after that blank screen. Nothing came atall.

```
sudo dpkg-reconfigure xserver-xorg
```

After running this command it says how to use dpkg and to use the help.

But nothing worked. 

After spending some time in google it seems that the problem is for NVIDIA Driver Update. Though I didn't found any solution and it seems like the solutions were for previous versions not for Lucid Lynx.

For reference I'm adding my configuation:
Intel Pentium D
Intel D945GCCR
1GB DDR2 Transcend RAM
WD 160GB HDD
XFX 9500GT 1GB DDR2
LG DVD Writer

I installed Ubuntu 10.04 from Live CD(GNOME). And was using it since few weeks. After many days I booted into Windows 7. Please help to get back my Ubuntu.

**UPDATE**

After posting this I just restarted and went to ubuntu to see if anything can be done

Now I get new error message in Low Graphics Mode error dialog box
[http://img175.imageshack.us/i/image0011g.jpg/](http://img175.imageshack.us/i/image0011g.jpg/)

I tried the recovery mode too...and tried the "failsafe graphics mode". But it didn't worked.

Then I went to console and typed ```
sudo dpkg-reconfigure -a xserver.xorg
``` and get this...
[http://img26.imageshack.us/i/image0013dt.jpg/](http://img26.imageshack.us/i/image0013dt.jpg/)
[http://img526.imageshack.us/i/image0014e.jpg/](http://img526.imageshack.us/i/image0014e.jpg/)

---

### Post by bashphoenux on 2010-05-19
Before installing any driver for ATI or nvidia, please make backup xorg.conf before following this method. 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

If you have edited this file but would like it to be automatically updated again, run the following command: 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Install the nvidia-settings package: 
```
 sudo apt-get install nvidia-settings
```
Download the nVidia driver: 
```
wget -O NVIDIA-Linux-x86-pkg1.run http://www.nvidia.com/Download/index.aspx?lang=en-us
sudo sh NVIDIA-Linux-x86-pkg1.run
```

---

### Post by krishnandu.sarkar on 2010-05-20
Ok, I went to recovery mode and dropped in to netroot(root console with n/w support)

> **bashphoenux said:**
> Before installing any driver for ATI or nvidia, please make backup xorg.conf before following this method. 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

The command says the file/path doesn't exist.

> If you have edited this file but would like it to be automatically updated again, run the following command: 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This command doesn't give any output but runned.

> Install the nvidia-settings package: 
```
 sudo apt-get install nvidia-settings
```

This command says I already have latest nvidia-settings installed.

> Download the nVidia driver: 
```
wget -O NVIDIA-Linux-x86-pkg1.run http://www.nvidia.com/Download/index.aspx?lang=en-us
```

Not sure what happend. But luks like this command downloaded NVIDIA-Linux-x86-pkg1.run 

> ```
sudo sh NVIDIA-Linux-x86-pkg1.run
```

This command output multiple lines saying !DOCTYPE doesn't exist and sumthing others doesn't exist, metadata not found etc. like this.

What to do now.

When I ran startx it's initializing KDE mode. Though after that nothing comes, just blank screen. But how's that possible?? I don't have KDE installed.

---

### Post by krishnandu.sarkar on 2010-05-20
Help guys. Please. What to do??

BTW I'm getting new error messages now [http://img97.imageshack.us/img97/671/image0015j.jpg](http://img97.imageshack.us/img97/671/image0015j.jpg)

---

### Post by Johnneylee on 2010-05-21
> **krishnandu.sarkar said:**
> Help guys. Please. What to do??

BTW I'm getting new error messages now [http://img97.imageshack.us/img97/671/image0015j.jpg](http://img97.imageshack.us/img97/671/image0015j.jpg)

I suggest you retry downloading and installing the NVidia drivers.

```
wget -O NVIDIA-Linux-x86-pkg1.run http://www.nvidia.com/Download/index.aspx?lang=en-us
```
Then
```
sudo sh NVIDIA-Linux-x86-pkg1.run
```
And finally, restart gdm:
```
sudo service gdm start
```

---

### Post by new-oldy on 2010-05-21
[SIZE=3]Just maybe the update didn't install properly and left something out.

It may be easier to download the live cd  and start again with a new installation.   [/SIZE]

[SIZE=3]Its just an idea and in the end worth a try.

Good luck !  :) :cool: :-\"
[/SIZE]

---

### Post by krishnandu.sarkar on 2010-05-21
Thank you [Johnneylee]("http://ubuntuforums.org/member.php?u=654390"), I've already tried those commands, suggested in IRC. Didn't Helped.

I re-installed it and updated. Now it's working perfectly fine. :)

@[new-oldy]("http://ubuntuforums.org/member.php?u=1077632") Lol...!! I did that atlas..!!

Thank you everyone for trying to help me out :)

---

