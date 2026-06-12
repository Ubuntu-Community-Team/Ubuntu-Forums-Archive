---
title: "Ubuntu 12.04LTS Server vs Desktop"
date: 2015-02-13
forum: Installation &amp; Upgrades
---

### Post by andrew198 on 2015-02-13
Hi


OK, I've just installed Ubuntu 12.04LTS Desktop on an old laptop. The purpose of this was manyfold:
1. To become acccustomed to Desktop environment. That's pretty much done now.
2. To improve my Linux command line skills & knowledge - ongoing. I'm currently altering network settings, installing programmes including using PPAs, etc., etc. All by using CL, not the GUI.
3. Use the laptop as a server for the following tasks: web server, seedbox (mainly using my LAN).


The first need is the seedbox. Having cracked that, I can hire extremely low cost dedi-servers with Ubuntu 12.04LTS Server installed and install a seedbox from scratch. The home laptop setup would be the practice run.


Now my question. Is there anything installed on the standard server installation of 12.04LTS that's not included in the desktop version. If so, what?
I want to make the server side of my desktop installation as close as possible to the standard server installation before continuing with the server side.
I would want initially openssh-server installed because I intend to setup the server from another PC connected to the LAN using Putty & SSH (to kind of replicate what I would have to do on a remote dedi-server). Does ssh come as standard on Desktop installation?


Many thanks

---

### Post by grahammechanical on 2015-02-13
> [COLOR=#000000]Now my question. Is there anything installed on the standard server installation of 12.04LTS that's not included in the desktop version. [/COLOR]

If there was no difference in the default software in the ISO image, then there would be no need for a desktop and a server edition.

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

I think with server edition installs decisions are taken during the install process as to what applications or types of server are required and then the applications are downloaded. 

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

Regards.

---

### Post by mörgæs on 2015-02-13
If the computer is old then Ubuntu 12.04 is probably the worst (=heaviest) of all Buntus to install. You could consider X/Lubuntu 14.04.1 in stead.

---

### Post by andrew198 on 2015-02-13
The speed seems fine. Certainly better than the Windows bloatware that was installed on it (and still is, it's now dual boot).

---

### Post by sandyd on 2015-02-14
> **andrew198 said:**
> Hi


OK, I've just installed Ubuntu 12.04LTS Desktop on an old laptop. The purpose of this was manyfold:
1. To become acccustomed to Desktop environment. That's pretty much done now.
2. To improve my Linux command line skills & knowledge - ongoing. I'm currently altering network settings, installing programmes including using PPAs, etc., etc. All by using CL, not the GUI.
3. Use the laptop as a server for the following tasks: web server, seedbox (mainly using my LAN).


The first need is the seedbox. Having cracked that, I can hire extremely low cost dedi-servers with Ubuntu 12.04LTS Server installed and install a seedbox from scratch. The home laptop setup would be the practice run.


Now my question. Is there anything installed on the standard server installation of 12.04LTS that's not included in the desktop version. If so, what?
I want to make the server side of my desktop installation as close as possible to the standard server installation before continuing with the server side.
I would want initially openssh-server installed because I intend to setup the server from another PC connected to the LAN using Putty & SSH (to kind of replicate what I would have to do on a remote dedi-server). Does ssh come as standard on Desktop installation?


Many thanks

By default, Ubuntu Server will ask you what software to install during the installation. This is done using a lovely program called tasksel.
You can install tasksel with the following command
```
sudo apt-get install tasksel
```
and use tasksel ```
sudo tasksel
```

By default, Ubuntu Desktop does not come with SSH.

Do not remember if OpenSSH Server is enabled by default in tasksel in 12.04, but if I remember correctly, it is not enabled by default in tasksel in 14.04.

Side note: This does not take into account imaged-installations of servers/vps/vds done in control panels such as solusvm, virtualizor, kiwivm, feathur, etc ,etc. For those, 99% of the time, ssh is enabled by default for remote access. To be sure that features you want are enabled, use tasksel after install or perform installation using VNC/iLO/KVM/IPMI or whatever they supply you with.

---

### Post by nerdtron on 2015-02-14
Getting accustomed to the command line takes patience.
It's not about how you memorize and copy/paste commands you found on the internet. (I'm pointing at you PPAs)
It's about how you understand the system and the commands you input. It's about, you know.. just...hhhmm...well.. hard to say.

I highly recommend reading the The Linux Command Line, for you to be familiar with the command line it self  (and how it works in general).
Very easy to read and to follow (trust me on this one). Grab the free PDF here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by andrew198 on 2015-02-14
Thank you all for your input and especially to grahammechanical for his links and sandyd. Tasksel does look interesting, but I'd rather install and setup all modules individually using CL (just for the practice). I can Google how to do that for each package. The server provider I'm considering (Kimsufi) I think just does a basic installation of Server, allowing users to then customise for their own use. So they don't include the likes of LAMP components, Ruby, email, Samba, etc. But they obviously do include OpenSSH otherwise I wouldn't be able to access via SSH. It is that state of the Server installation that I want to start with.


The pdf that you quote nerdtron, I downloaded many months ago and have been studying it and practising using an existing seedbox of mine via SSH. But I don't have root access on that, so many of the commands have been redundant for me. It is an excellent manual and it takes a step by step approach from nerd status through to programming.

---

### Post by sandyd on 2015-02-14
> **andrew198 said:**
> Thank you all for your input and especially to grahammechanical for his links and sandyd. Tasksel does look interesting, but I'd rather install and setup all modules individually using CL (just for the practice). I can Google how to do that for each package. The server provider I'm considering (Kimsufi) I think just does a basic installation of Server, allowing users to then customise for their own use. So they don't include the likes of LAMP components, Ruby, email, Samba, etc. But they obviously do include OpenSSH otherwise I wouldn't be able to access via SSH. It is that state of the Server installation that I want to start with.


The pdf that you quote nerdtron, I downloaded many months ago and have been studying it and practising using an existing seedbox of mine via SSH. But I don't have root access on that, so many of the commands have been redundant for me. It is an excellent manual and it takes a step by step approach from nerd status through to programming.

Kimsufis (and most of other OVH servers) are clean,basic installs with OpenSSH - the only thing that is different is that OVH uses their own special kernel. It may or may not have issues depending on what kernel modules you use.

---

### Post by andrew198 on 2015-02-14
> **sandyd said:**
> Kimsufis (and most of other OVH servers) are clean,basic installs with OpenSSH - the only thing that is different is that OVH uses their own special kernel. It may or may not have issues depending on what kernel modules you use.


Kimsufi offer a wide selections of distos, including Ubuntu, CentOS, Debian, Fedora, etc., etc. Surely if they install Ubuntu, then it has to use Linux kernal 3.8.8, otherwise it's not Ubuntu?

---

### Post by sandyd on 2015-02-14
> **andrew198 said:**
> Kimsufi offer a wide selections of distos, including Ubuntu, CentOS, Debian, Fedora, etc., etc. Surely if they install Ubuntu, then it has to use Linux kernal 3.8.8, otherwise it's not Ubuntu?

No,
A kernel does not define an Linux distribution. I could compile and install the latest version of the linux kernel [from the git repo that houses the source code for Kernel 3.x]("https://github.com/torvalds/linux"), on Ubuntu, and it would still be Ubuntu.

OVH uses a 'hardened' kernel that they make themselves. Unfortunately, it has no support for some features and is missing some modules that some people might require. The people who need these features/modules can revert to the regular kernel to fix this.

---

