---
title: "Ubuntu 12.04 update problem"
date: 2012-11-20
forum: Installation &amp; Upgrades
---

### Post by a.kazemi on 2012-11-20
I have installed fresh copy of Ubuntu 12.04 x64bit and have  some problems with the lightdm after some struggling I finally installed  nvidia-current and nvidia-setting by adding 

> [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu)to  repositories. then everything seemed good and then I have started to get  and install required softwares and packages from Ubuntu software  Center. I need almost scientific computation related packages like  eclipse, scilab, wxmaxima and... . all of them installed very good but  Scilab doesn't start it returned an error like "scilab can not find its  main classpath" and some errors related to java library missing. then I  removed it. also I cannot run nvclock software which was a package for  Nvidia graphic card controlling and everclocking. I have installed CUDA  toolkit and run it very good and still it works fine. the main problem: after these installations when I run sudo nautilus in command prompt I  give this error:[INDENT]   > Initializing nautilus-gdu extension   Nautilus-Share-Message: Called "net usershare info" but it failed:  'net usershare' returned error 255: Ignoring unknown parameter "server  role"   net usershare: cannot open usershare directory  /var/lib/samba/usershares. Error No such file or directory   Please ask your system administrator to enable user sharing. [/INDENT]also when I run update manager it gives me error that it can not  install all updates and suggest partial upgrade. when I do it it  upgrades my 12.04 ubuntu to 12.1 version and also it have many problems.  I recovered my 12.04 version again and try ro run update but after  updating about 400 Mb also many problems occured, too.
  I try to run these codes which was suggested for fixing this problem:[INDENT]   > sudo apt-get install aptitude
sudo aptitude update   
sudo aptitude dist-upgrade [/INDENT]but aptitude tell me, it wants to remove some libraries and packages  and the nvidia-current! which is very important for me and it doen't  want to update or upgrade nvidia-current! 
  please help me now I can not update my ubuntu...

---

### Post by ibjsb4 on 2012-11-20
May just want to wait a while.

[Partial upgrade]("http://ubuntuforums.org/showthread.php?t=1859240")

---

### Post by a.kazemi on 2012-11-20
> **ibjsb4 said:**
> May just want to wait a while.

[Partial upgrade]("http://ubuntuforums.org/showthread.php?t=1859240")

Thanks for the link. I do not understand whats should I do now? it says wait for couple of hours but even after somedays I face the problem again and again and cannot update my ubuntu because partial upgrade packages wants to be updated

---

### Post by cwsnyder on 2012-11-20
You do not have the full path for the repository you added.  It must tell your repository what version of Ubuntu you want to upgrade.  The correct path for the ppa should look something like: ```
http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main binary-amd64
```There may or may not be more slashes and other punctuation in the ppa call.

Also, your apt-get line is messed up badly for execution.  It should read:```
sudo apt-get update && sudo apt-get install aptitude && sudo aptitude update && sudo aptitude dist-upgrade
```You may also use apt-get for the entire line, as such:```
sudo apt-get update && sudo apt-get dist-upgrade
```Also, did you do a ppa-install? Or did you at least download and install the GPG key for the repository?  If you don't know what I am talking about in the last two questions, you should spend a LOT of time reading up about ppa repositories before you attempt to install another, or follow directions _exactly_.

---

### Post by dannyboy79 on 2012-11-20
i think first we need to understand what you really want. Do you really want to upgrade to the latest bleeding edge ubuntu? 12.04 is a Long ZTerm Support release so it's supported for 5 years. If you want to stick with an LTS release then stop trying to upgrade to 12.10. Don't issue dist-upgrade, just do normal updates.

---

### Post by a.kazemi on 2012-11-20
> **dannyboy79 said:**
> i think first we need to understand what you really want. Do you really want to upgrade to the latest bleeding edge ubuntu? 12.04 is a Long ZTerm Support release so it's supported for 5 years. If you want to stick with an LTS release then stop trying to upgrade to 12.10. Don't issue dist-upgrade, just do normal updates.

I do not want to upgrade to 12.1, I just want to update my 12.04 ubuntu as usual but when I open update manager it try to upgrade my ubuntu and the softwares. at this time I have some errors around my ubuntu like the nautilus which I have mentioned above also I have problem with eclipse it cannot connect to its repositories and check for update but the link I give it for the repository is correct and I have installed its toolkits from that link before this problem emerged.

now my main problem is updating! I can not update ubuntu as usual and when I try to do it with update manager it try to upgrade my ubuntu

---

### Post by cwsnyder on 2012-11-20
It tries to upgrade Ubuntu because that is the choice you picked. If you have Synaptic package manager loaded, go to Settings >> Repositories >> Update Tab.  At the bottom of the screen, there is a selection box for *Notify me of a new Ubuntu version* followed by a pull down box where you can specify: *for any new version*, or *for long-term support versions*, or *Never*.  Select For long-term support versions or Never to stop updating to QQ 12.10.

---

### Post by a.kazemi on 2012-11-20
> **cwsnyder said:**
> It tries to upgrade Ubuntu because that is the choice you picked. If you have Synaptic package manager loaded, go to Settings >> Repositories >> Update Tab.  At the bottom of the screen, there is a selection box for *Notify me of a new Ubuntu version* followed by a pull down box where you can specify: *for any new version*, or *for long-term support versions*, or *Never*.  Select For long-term support versions or Never to stop updating to QQ 12.10.

thanks dear friend I know that and have checked it before. "for long-term support versions" is selected and still it wants to upgrade.
I use Ubuntu Software Center which is officially comes with 12.04 instead synaptic.

---

### Post by ibjsb4 on 2012-11-20
Just to be clear.

Dist-upgrade will not perform a release upgrade (#3).

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by dannyboy79 on 2012-11-20
> **ibjsb4 said:**
> Just to be clear.

Dist-upgrade will not perform a release upgrade (#3).

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)
oh, I believe the dist-upgrade did upgrade the distribution at one time or another, maybe not. Dunno.

Have you tried to fix broken pacakges with this?
```
apt-get -f install
```

---

### Post by a.kazemi on 2012-11-20
> **dannyboy79 said:**
> oh, I believe the dist-upgrade did upgrade the distribution at one time or another, maybe not. Dunno.

Have you tried to fix broken pacakges with this?
```
apt-get -f install
```

no I haven't tested it and am going to do and will report the result but before this I have to mention something important, maybe all these issues emerged after trying to install samba package! with these commands in terminal:

> sudo apt-get install samba

I can't remember why I want to install it but one of the problems that exist in my system and exactly appear when partial upgrade message comes up is the problem report request and when I click report button Ubuntu internal error message appears as bellow:

> Sorry, Ubuntu 12.04 has experienced an inrernal errorin details it is written: 
> ExecutablePath:
/usr/sbin/samba_dnsupdate
Package:
samba4 4.0.0-beta2+dfsg1-3
Problem Type:
Crash
Title: samba_dnsupdate crashed with RuntumeError in get_credentials(): kinit for Ubuntu$@UBUNTU-DOMAIN failed (Cannot contact any KDC for requested realm)
....Is this the source of my problems?

---

### Post by dannyboy79 on 2012-11-20
I don't believe the samba error would be the cause, no

---

### Post by ibjsb4 on 2012-11-20
According to [this]("http://packages.ubuntu.com/search?keywords=samba4") you are running 12.10.  Open a terminal and please verify.

cat /etc/issue

And I would like to see what all you do have for sources.  So if you would once again in terminal (copy and paste).

find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \

AND ..

sudo apt-get update

Please post the outputs of the two commands.

---

### Post by cwsnyder on 2012-11-20
@dannyboy79 : Read the man page for apt-get.  dist-upgrade does not change the distribution release until the /etc/apt/sources.list file is changed.  dist-upgrade just loads all files and dependencies, sometimes fixing broken packages.

---

### Post by a.kazemi on 2012-11-21
> **dannyboy79 said:**
> I don't believe the samba error would be the cause, no

last night at first I tried to install samba again by the 
> sudo apt-get install samba 
command in terminal and after installation became complete I remove it by this:
> sudo apt-get remove samba

after that I haven't gotten the internal system error again! then I unchecked these two option from "software sources" under the "Ubuntu Software" tab which were checked before this:
> Proprietary drivers for devices (restricted)
Software restricted by copyright or legal issues (multiverse)

then before checking for update I changed the download from address before it was: 
> United States : 76.73.4.58
I changed it to:
> United States: [http://mirror.pnl.gov/ubuntu](http://mirror.pnl.gov/ubuntu)

after these when I checked for update with Ubuntu update manager it find just 64 Mb update instead of 450 Mb update which had been founded before these. I applied these updates and restart my system. everything seems good now even I installed Scilab again which have given me error and didn't start before now I can start and use it. no nautilus warning appear also I can update eclipse as before!
:guitar:

I execute this command after all of these works and nothing happen:
> sudo apt-get -f install

but now I believe that everything comes out from bad installation of samba! and if before doing these works if I have used this command it would find samba corrupted packages and try to fix them so I think the command was my solution.

thanks a lot guys I couldn't do it without your hints

---

### Post by a.kazemi on 2012-11-21
> **ibjsb4 said:**
> According to [this]("http://packages.ubuntu.com/search?keywords=samba4") you are running 12.10.  Open a terminal and please verify.

cat /etc/issue

And I would like to see what all you do have for sources.  So if you would once again in terminal (copy and paste).

find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \

AND ..

sudo apt-get update

Please post the outputs of the two commands.


the Problem is solved however I try your command 
th ubuntu version is:
```
hpc@ubuntu:~$ cat /etc/issue
Ubuntu 12.04.1 LTS \n \l

```

I said that I myself try to install samba it hadn't came with my ubuntu 12.04 installation

the application list get too much long do really want it?:confused: if yes I execute it again

---

### Post by a.kazemi on 2012-11-21
excuse me, I have found out that samba_dnsupdate is still running on my system. but I have removed samba how I can remove it completely?
it is under this directory:

> /usr/sbin/samba_dnsupdateand I find a directory of its files here:

> /etc/samba

or is it the OS main software for sharing and shouldn't be removed?!

---

