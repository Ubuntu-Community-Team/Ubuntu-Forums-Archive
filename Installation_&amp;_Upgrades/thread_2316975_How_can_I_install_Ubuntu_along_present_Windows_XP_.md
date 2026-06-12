---
title: "How can I install Ubuntu along present Windows XP on disk D (not C)?"
date: 2016-03-12
forum: Installation &amp; Upgrades
---

### Post by artss2 on 2016-03-12
I want to install Ubuntu 10.04 on Disk D (that has about 3-4gb, and I can free more), but C- has just several hundreds of mbs of free space. How can i do no  it from Ubuntu iso (cd)? Is there option, should I make some partition, and could I recover (roll back) my disk if something would go wrong?

---

### Post by Edison_James on 2016-03-12
> **artss2 said:**
> I want to install Ubuntu 10.04 on Disk D (that has about 3-4gb, and I can free more), but C- has just several hundreds of mbs of free space. How can i do no  it from Ubuntu iso (cd)? Is there option, should I make some partition, and could I recover (roll back) my disk if something would go wrong?

3-4 gb is really not enough for ubuntu, but more to the point, ubuntu 10.04 is a very old version, I would recommend something newer, if you wait another month 16.04 should be available which is an LTS version.

---

### Post by ajgreeny on 2016-03-12
10.04 is now long out of date so there is no point in installing that version; you will not be able to install any packages to it nor update it any more.

Try 14.04, and if you do not like the unity desktop, which may be too resource intensive for an old XP machine anyway, try Xubuntu or Lubuntu 14.04.

You need more space than 3 or 4 GB for these, so unless you can make free space of at least 6GB or thereabouts you will be wasting your time as far as actually using the OS in a meaningful way is concerned.

Show us how much space you have on the hard disk by running X(L)ubuntu 14.04 as a live system, opening a terminal and typing **sudo fdisk -l** in that, hitting Enter, and copying the output shown back here by highlighting it with mouse and copying with a right click.

---

### Post by RobGoss on 2016-03-12
Well my first question is why would you even consider still using Windows XP, there's no support for this operation any more.

I'm not sure what is the amount of space you have on your existing hard drive it might be best to just to install a fresh installation on that hard drive of Ubuntu 16.04 which will be fully released in just a few weeks. But in the mean time you can install the Beta version for a 64 or 32- bit machine which i'm assuming you have a 32-bit seeing you still have **Windows XP** on it.

I do advise you to have more space then **_3 or 4 GB_** if you want to fully enjoy what Ubuntu has to offer.

**Ubuntu 16.04 Xenial beta**
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by grahammechanical on 2016-03-12
When we change partition sizes whether in Windows or Linux there is no simple "roll back function." This is why we are warned of possible data lost. This is why we backup our data that we cannot afford to loose.

If we have 2 hard drives and we do not want to over-write what is on one hard drive as we install Ubuntu, then we can always disconnect the hard drive that we want to protect. Then the Ubuntu installer will only see one hard drive. The hard drive we want to install Ubuntu on.

After installation we reconnect the other drive and use the BIOS setup utility to boot from the Ubuntu drive. Then when we are in Ubuntu we open the terminal and run

```
sudo update-grub
```

We will be asked to put in our password. It will not be printed to the screen for security reasons but it will be accepted. The command will run and we will see a printout that will list Windows as well as Ubuntu.

Now, when we reboot we will see a Linux boot menu (Grub) and we can select to load either Ubuntu or Windows.

Regards

---

### Post by artss2 on 2016-03-12
My intel is non-pae so I can use just ubuntu 10.4, xubuntu 12.4 as the latest. I used vbox image of it and they take no more than 3 gb as bare minimum that I need just with gcc compiler. And I have read that Ubuntu has 3 installation options: demo/live, partition one and third one - just along the windows system so I assume without partition. My pc has one hard disk with C, D, E sections (partitions?). And I need it for very simple task and probably short time. As in vbox i cannot reveal eth0 by the means of lipcap so I hope without virtual environment I would do it. Except it my pc has about 10 years, intel came very hyperheated frequently as my 3.3 voltage came very low, when I installed ubuntu on virtual machine, and when installed additionally codeblocks the pc screen came black so I was impossible to install ide by packages, so I used ready images, but untill now in vain.

In vain to find eth0 device on ready image where technical problems do not reveals explicitly. But concurrent installation of different os may aggraves it critically?

---

### Post by Edison_James on 2016-03-13
> **artss2 said:**
> In vain to find eth0 device on ready image where technical problems do not reveals explicitly. But concurrent installation of different os may aggraves it critically?

It sounds like you need a very very lightweight distro. Also if your pc is 10 years old or more and overheating that is an indication that you need a new cooling fan.

---

### Post by artss2 on 2016-03-13
So there is simple way out theoretically. To use wibu. But when I freed up to 4 gb and launched wibu installer (despite it needs just 3 gb), waited several minutes twice in such way, and in the very end of such install (0s remained) I got such error -ubuntu  installer an error occurred http error 404: not found   for more information please see the log file. So what this error means, what http? Can I use already fully installed wibu? What is the normal way to install wibu?

---

### Post by yancek on 2016-03-13
Wubi is a program which you can install in windows and run Ubuntu as a program  inside windows.  It has been discontinued and is no longer supported and you are not likely to get much support trying to use it.  I believe it originally worked on xp so you might get it to work.  the 404 error means the site you were looking for was not found. The problems with this is you are using an outdated/unsupported system on the computer; windows xp and trying to use a no longer supported program (wubi) to install a no longer supported version of Ubuntu.

---

### Post by oldos2er on 2016-03-13
Do not use Wubi; it is no longer supported, neither is 10.04. Try Lubuntu: [https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

---

### Post by artss2 on 2016-03-14
I tried to install ubuntu from demo mode. There was option to side by side installation so i quited as I did not know could I uninstall it, should it make additionally new partitions along with c, d, e ones. Should I loss some data anyway? But why I should not use wubi - i need it for very short time. Windows xp and old ubuntu is outdated but I use it.

If that http resource was last one in wibu install could I force using wibu. If there would not this error what i would do the next - reboot and it installation would appear.

Do ubuntu 14.04 supports wubi? Internet tells that yes (just 13.04 do not) but in iso file I cannot find wubi.exe?

---

### Post by hakuna_matata on 2016-03-14
> **artss2 said:**
> Do ubuntu 14.04 supports wubi? Internet tells that yes (just 13.04 do not) but in iso file I cannot find wubi.exe?
The desktop isos of 14.04 contain a wubi.exe. e.g.: [URL="http://releases.ubuntu.com/14.04/ubuntu-14.04.3-desktop-i386.list"]file list of ubuntu-14.04.4-desktop-i386.iso
[/URL]
There is also a wubi.exe at the bottom of the [URL="http://releases.ubuntu.com/14.04/"]official download site for 14.04
[/URL]
But there is no real official maintainance and support.
> **artss2 said:**
> Windows xp and old ubuntu is outdated but I use it.
I don't recommend the use of old and outdated versions especially if you use internet with these versions. But I know, there are a lot of users who also still use old and outdated versions.

That was one of the reasons why I decided to help Wubi users. In a lot of cases it is really not necessary to use old and outdated versions. 

So if you intend to use old and outdated versions, better try Wubi versions from [here]("https://github.com/hakuna-m/wubiuefi/wiki#releases") and install a current version.

But IMHO 3-4GB is not enough free space for a Wubi installation. You should have at least 5GB and try Lubuntu instead of Ubuntu.

---

### Post by artss2 on 2016-03-15
So, wubi of 10.4 take 3gb, but need 4 gb for installation. So what is requirement of 14.04? In gb (real and formal)?
Accordingly to [http://releases.ubuntu.com/14.04/ubuntu-14.04.3-desktop-i386.list](http://releases.ubuntu.com/14.04/ubuntu-14.04.3-desktop-i386.list) wubi.exe is in root directory, but I did not see it my iso iamge

---

### Post by hakuna_matata on 2016-03-15
> **artss2 said:**
> So, wubi of 10.4 take 3gb, but need 4 gb for installation. So what is requirement of 14.04? In gb (real and formal)?

Default minimum installation size is now 5GB and you need about 6GB free space, but IMHO this minimum size is only needed for Ubuntu. Lubuntu needs less size but default minimum size is the same. But you can skip size check:
```

cd folder_of_wubi.exe
wubi.exe --skipsizecheck
 
```
You can try if less space also works. I haven't never tried it.

After installation of Lubuntu with installation size 5GB (6GB free space)
```
df -h
```
shows
```

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0      4,5G  2,1G  2,1G  51% /
```

> **artss2 said:**
> Accordingly to [http://releases.ubuntu.com/14.04/ubu...ktop-i386.list]("http://releases.ubuntu.com/14.04/ubuntu-14.04.3-desktop-i386.list") wubi.exe is in root directory, but I did not see it my iso iamge
Maybe, no desktop image ?

---

### Post by artss2 on 2016-03-16
If not desktop, so which one? Server -no. Moreover about server - i downloaded 10.4 and 14.4 server and the last is less in size than first one (unfortunately i have opportunity to try it).

---

### Post by Edison_James on 2016-03-16
> **artss2 said:**
> If not desktop, so which one? Server -no. Moreover about server - i downloaded 10.4 and 14.4 server and the last is less in size than first one (unfortunately i have opportunity to try it).

The server version comes without a GUI, which accounts for it's smaller size. It's not what you want.
I use lubuntu myself, very happy with it.

---

### Post by hakuna_matata on 2016-03-16
> **artss2 said:**
> If not desktop, so which one? Server -no.
I meant the server version. But I didn't mean, you should try it with Wubi. It contains no Wubi but it also doesn't work with Wubi.

But if the file list contains a wubi.exe and your matching .iso doesn't contain a wubi.exe, then something is wrong.

---

### Post by gordintoronto on 2016-03-16
You really should just spend a little money. Where I live, there are several stores which sell off-lease computers for less than $130 (Canadian, about $100 U.S.) which will run Xubuntu -- and probably any of the Ubuntu family -- extremely well.

If that's too much for you, you could buy a hard drive for about $50. Make sure you get the right type, probably IDE.

---

### Post by artss2 on 2016-03-17
To make the situation more clear I need note i am not from USA/Canada. And I need it for a temporal task that I should did a week ago. But as I  spent about month for making workable lpcap on virtual ubuntu or live cd i need to do it anyway. Maybe fedora could not produce "no suitable device found" despite it is present and revealed by ifconfig and tcpdump. Maybe it is due that despite my network card is present on my pc but I have no wired connection with local net or internet just 3g-modem. Anyway the real problem is in root privileges. As after destroying it by chmod 777 i see at least usbmon0 device.

---

### Post by sudodus on 2016-03-17
Maybe you will get better help if you tell us what you really want to or have to do :-)

Instead of focusing on a system setup which involves tools that are no longer supported, we can try to help you directly - if you ask about that 'temporal task'.

---

### Post by artss2 on 2016-03-17
I have created several unanswered topics about it on the forum. The main issue to create lpcap application using eth0 interface. But if Ubuntu gcc produce no suitable devices on desktop what I can do. No eth0, nor lo, neither usbmon1, despite tcpdump and if configure show them, at least eth0, lo.

---

### Post by sudodus on 2016-03-17
Do you want to do something like this?

[http://www.tcpdump.org/pcap.html](http://www.tcpdump.org/pcap.html)

Maybe you can get better help in the programming forum, or the network forum or the security forum?

In that case, make a new thread with a descriptive title and a good description of you main problem in the opening post, or re-activate an old thread by 'bumping' it - write a new post to put the thread in the list of [New Posts](http://ubuntuforums.org/search.php?do=getnew&contenttype=vBForum_Post)

---

### Post by goofprog on 2016-03-17
> **artss2 said:**
> To make the situation more clear I need note i am not from USA/Canada. And I need it for a temporal task that I should did a week ago. But as I  spent about month for making workable lpcap on virtual ubuntu or live cd i need to do it anyway. Maybe fedora could not produce "no suitable device found" despite it is present and revealed by ifconfig and tcpdump. Maybe it is due that despite my network card is present on my pc but I have no wired connection with local net or internet just 3g-modem. Anyway the real problem is in root privileges. As after destroying it by chmod 777 i see at least usbmon0 device.

If it is a wireless adapter you are using try wireshark.

---

### Post by artss2 on 2016-03-20
It is probably means nothing to use wubi in this situation as when launched xubuntu 14.04 I got "no interface found". So I cannot understand what is the reason of it. Even ubuntu server 10.04 returns it anyway??

---

