---
title: "Live USB Installation - Can't Login - LUBUNTU"
date: 2017-08-23
forum: Installation &amp; Upgrades
---

### Post by guzmanlinux on 2017-08-23
Hello,

I'm new to the linux world. 
I was testing (trying without installation) **Lubuntu-17.04.**

It asks for a username and password, for what I've read, in this case the default is:
- user: lubuntu
- password: no password, left blank.
[https://askubuntu.com/questions/103896/live-cd-asks-for-a-username-and-password](https://askubuntu.com/questions/103896/live-cd-asks-for-a-username-and-password)

But after entering the credentials, it doesn't continue and it asks for the credentials again. I can't login.
Attached are images of the process.

What could be happening?

THANKS!!

PC: Acer Aspire One (netBook), 1 GB RAM

---

### Post by sudodus on 2017-08-23
Welcome to the Ubuntu Forums :-)

Please describe how you created the live USB drive.

- Which iso file?

- Did you check with md5sum that the download was successful? [help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

- Which **tool/method** did you use to create the live USB drive?

---

### Post by guzmanlinux on 2017-08-23
Hello *sudodus*! Thanks for the reply and welcome.

I answer your questions below.

**- [COLOR=#000000]Please describe how you created the live USB[/COLOR]**
I used Rufus 2.16 ([https://rufus.akeo.ie/?locale](https://rufus.akeo.ie/?locale)) to create a LIVE USB.
I don't know if it matters, but I used the Windows (Win 7 Starter) PC to create it.

[COLOR=#000000]**- Which iso file?**
[/COLOR]I downloaded the ISO file from the Lubuntu website ([https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)), using a torrent: lubuntu-17.04-desktop-i386.iso
I chose the 32bit.

[COLOR=#000000]**- Did you check with md5sum that the download was successful?**
[/COLOR]No, I have no idea what md5sum is, I've never used a terminal (well...maybe DOS 20 years ago). I've read something about md5sum, but don't know what to do.
How can I check if I can't login? For what I've read you need the linux terminal to check.

**[COLOR=#000000]- Which [/COLOR]****[B]tool/method did you use to create the live USB drive?**
[/B]Rufus 2.16

[U]Let me provide additional info.

[/U]I continued today with the Hard Drive installation and many things happened (maybe this require another post, if yes, just mention and I'll proceed).

1) When selecting the Wifi network and introducing the password, it doesn't connect (tried with 2 different networks)
2) When trying to encrypt the disk an error occurs: *Unsafe swap space detected*. Have seen some solutions online but didn't implement them because I cannot try Linux (because of the looping authentication issue)
3) Ok, I didn't encrypt, instead I selected LVM, but this error occured: [I][COLOR=#000000][FONT=Verdana]Unexpected error while creating volume group[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Autopartitioning using LVM failed... [/FONT][/COLOR][/I][https://bugs.kali.org/view.php?id=1674](https://bugs.kali.org/view.php?id=1674)
4) Another error later: ubi-platform failed, exit code 141. Further info: /var/log/syslog
5) Another error: [I]Installer encountered an error copying files to hard disk (error 5) input/output error, faulty CD/DVD or kard disk...
[/I]

Well, as you can see, my first encounter with Linux has been a little bit problematic.

Any thoughts are welcome :KS

---

### Post by sudodus on 2017-08-23
0. You can copy and paste command lines from here. (Command lines are often easier when helping compared to describing how to use graphical application (GUI) programs.)

1. Rufus is a good tool to make USB boot drives in Windows.

2. For your Acer Aspire One (netBook), 1 GB RAM, I would suggest that you select another version of Lubuntu, 16.04.1 LTS, which has the longest support time until end of life (of the versions that are supported now). It is debugged and polished, when after installation you have made it up to date via a graphical user interface or the following command lines.

You can find this version via the link: [How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865)

The program md5sum calculates and displays the md5 checksum (to compare with the listed value via the website link in my first post (post #2).

```
$ md5sum lubuntu-16.04.1-desktop-i386.iso 
**72a400913ba0ed59b88c42e5aab629e9**  lubuntu-16.04.1-desktop-i386.iso
```

I think Rufus can calculate and show the md5sum in Windows.

3. I suggest that you make a standard installation and avoid LVM and avoid all encryption, at least while you take the first steps with linux. Install a basic system and learn how to use it. Later on you can install more advanced systems.

4. If possible, you should connect the netbook via wired internet (ethernet cable) during the installation and in the beginning after the installation. Via wired internet you can update and upgrade to make it up to date and after that install additional software, for example a suitable driver for the wifi.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

You may prefer to use the Synaptic Package Manager, which is a graphical front end.

---

### Post by guzmanlinux on 2017-08-23
Hello!

Thanks for the fast reply.

I'll check all the info provided and will reply to you as soon as possible with an update.

---

### Post by guzmanlinux on 2017-08-23
Hello *Sudodus*,

I tried an older version, [COLOR=#000000]Lubuntu, 16.04.1 LTS [/COLOR]and it worked fine.

This happened:

1) When trying it, it didn't ask me to login.
2) When trying to encrypt, this error happened again: *Unsafe swap space detected.*

But in general terms it works ok.
Thanks for your help.

PS. I don't see a button to upvote your answer!

---

### Post by sudodus on 2017-08-23
> **guzmanlinux said:**
> Hello *Sudodus*,

I tried an older version, [COLOR=#000000]Lubuntu, 16.04.1 LTS [/COLOR]and it worked fine.

This happened:

1) When trying it, it didn't ask me to login.
2) When trying to encrypt, this error happened again: *Unsafe swap space detected.*

If you want to try encryption later on, I would recommend LVM with encryption (not encrypted home). And I suggest that you use the lubuntu alternate iso file to install it,

```
lubuntu-16.04.1-alternate-i386.iso
```
> 
But in general terms it works ok.
Thanks for your help.

PS. I don't see a button to upvote your answer!

Thanks for sharing your solution! I'm glad I could help you :-)

There is no upvote button in the Ubuntu Forums. You have already discovered how to mark this thread as SOLVED. That's all you need to do. It does not mean that the thread is closed; you can ask about or discuss something related later on.

But if you want help with a different problem, it is better to start a new thread with a good descriptive title. That way you have better chances to get the attention of people who know about that particular problem.

---

