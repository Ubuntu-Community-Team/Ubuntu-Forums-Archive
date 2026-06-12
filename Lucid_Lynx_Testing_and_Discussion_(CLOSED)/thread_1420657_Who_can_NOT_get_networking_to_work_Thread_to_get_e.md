---
title: "Who can NOT get networking to work? Thread to get everyone networked by Beta!"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-03-03
I just tried again, to get 3 PC's and a wireless netbook to connect, un Ubuntu Karmic, Lucid and WinXPSP3.  All have same "workgroup" name, some have directory folders shared, Printer is set to share.  

I get:[B]
No printing remotely. 
No file access at all. 
Some Workgroup names do appear.[/B]

I am willing to set a test environment to work on this again.

Those of you who can not get Samba (or whatever Lucid network client) to successfully transfer files and to print remotely, please chime in.

Those who want to assist, please do so also.

First, will someone please post what exact information we need to post to begin the diagnosis; a standard list for those who can't network to check, and optionally attach?

Inspired by this thread:
[http://ubuntuforums.org/showthread.php?t=1392793&highlight=nautilus](http://ubuntuforums.org/showthread.php?t=1392793&highlight=nautilus)

---

### Post by emarkay on 2010-03-10
FWIW, I have had this issue for a few years.

I am sure it's something simple, never been important enough to focus on, but have tried a few times, including posts here and Launchpad bug submissions.

I even cleaned out 2 PC's to work with debugging, but no one offerd assistance.

One would think a core OS feature; even if only a few can't get it, would be more important than the fluffy things like login screens, and online music stores...

Oh well...

---

### Post by whoop on 2010-03-10
Samba is not working properly for me (client 10.04 attempting to connect to 9.10 server)

bugreport:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/532024](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/532024)
bugreport upstream:
[https://bugzilla.gnome.org/show_bug.cgi?id=612202](https://bugzilla.gnome.org/show_bug.cgi?id=612202)

---

### Post by NCLI on 2010-03-10
If samba isn't working properly for you, I'd recommend using SSH instead. I haven't had a networking problem since I dropped Samba.

---

### Post by whoop on 2010-03-10
> **NCLI said:**
> If samba isn't working properly for you, I'd recommend using SSH instead. I haven't had a networking problem since I dropped Samba.

I use ssh, just not for file sharing...

---

### Post by cariboo on 2010-03-10
We should know what your setup is, do you have a server? or are you just connecting between a windows computer and a Ubuntu computer? Is it a direct connection via a crossover cable or through a router? Static or dynamic ip addresses?

---

### Post by whoop on 2010-03-10
> **cariboo907 said:**
> We should know what your setup is, do you have a server? or are you just connecting between a windows computer and a Ubuntu computer? Is it a direct connection via a crossover cable or through a router? Static or dynamic ip addresses?

ubuntu server (9.10), ubuntu desktops (10.04), static ip addresses, router.

2 Ubuntu desktops (9.10), arch desktop, debian lenny desktop, fedora 12 desktop are all working fine, it's just the 10.04 desktops.

---

### Post by emarkay on 2010-03-10
> **cariboo907 said:**
> We should know what your setup is, do you have a server? or are you just connecting between a windows computer and a Ubuntu computer? Is it a direct connection via a crossover cable or through a router? Static or dynamic ip addresses?

Well this is how I officially started this:
[https://answers.launchpad.net/ubuntu/+source/samba/+question/87080](https://answers.launchpad.net/ubuntu/+source/samba/+question/87080)

They "passed the buck" and made the Bug a Question.

5 computers, 2 desktops (wired) , 2 laptops (wired or wireless), 1 Netbook (wireless).
 3 with Ubuntu Karmic and Lucid and Win XPSP3, 1 with Karmic only and WinXP, one with XP only.  No server, just have a Linksys WRT54GL router.  I have been able to get Windows to network to Windows in the past, so I know it's possible...

IP addresses; on the network?  I thought "intranet" IP's were static?  Not too "hip" on the depths of the protocol (otherwise I'd have figured this out by now...).

Thanks.

---

### Post by timosha on 2010-03-10
> **cariboo907 said:**
> We should know what your setup is, do you have a server?

I can also give my setup, but that is not the issue. The issue is that it works in 9.10 and that it worked in the first 10.04 alpha.

So, the issue is that it is a regression bug, like so many other bugs in 10.04 (it works, and then suddenly it doesn't work anymore).

---

### Post by Sophont on 2010-03-10
> **timosha said:**
> 
So, the issue is that it is a regression bug, like so many other bugs in 10.04 (it works, and then suddenly it doesn't work anymore).

Fairly normal. It's an alpha version. Lots of packages get upgraded - there is always some breakage going along with that, which then needs to get fixed before release.

That's not to say you shouldn't raise the issue. That's also what alpha versions are about. Just that the above remark sounds like you think there is something terribly gone wrong when an alpha version has occasional regressions.

Anybody who's not comfortable with breakage during dev cycles - wait for the release version.

---

### Post by timosha on 2010-03-10
> **Sophont said:**
> 

That's not to say you shouldn't raise the issue. That's also what alpha versions are about. Just that the above remark sounds like you think there is something terribly gone wrong when an alpha version has occasional regressions.

.

I am retired and I spend 4 to 6 hours daily on testing Ubuntu 10.04 (and reporting bugs). So, I have a slight idea what an alpha release means and I even know how to test alpha and beta releases. But regression bugs are frustrating.

That said, this bug is not even an Ubuntu bug. It is a Gnome gvfs bug and Canonical points to gnome.org for a solution.

---

### Post by Sophont on 2010-03-10
> **timosha said:**
> But regression bugs are frustrating.

Yes - they are.

---

### Post by cariboo on 2010-03-10
My comment was most directly pointed to emarkay, as he seems to be the one doing most of the complaining.

Samba does work on 10.04. I have my network setup the classic way, with an smb.conf file. I do it that way, because I find it easier to setup. BTW I installed Lucid UNR last night, and installed my Epson R340 attached to a Windows XP system with less trouble than my networked Brother Laser printer.

With windows there is not much to do except setup the shares properly, and make sure all the computers on the network are in the same workgroup. Depending on what version, Home/Pro you are using, the workgroup is set to MSHOME in the home versions and WORKGROUP in the pro versions. Another thing I do is assign the computers names, so they are easier to find than the default names that Windows assigns the system

The next thing you need to make sure of is that all the computers on the network have an ip address that is in the same netblock. Using a router for DHCP solves that problem for most networks, but if you have set any static ip addresses make sure that are also in the same netblock, for instances if you router assigns addresses in the 192.168.1.1 - 192.168.1.100 range, static ip address should be in the 192.168.1.101 - 192.168.1.254 range. One other thing to do is make sure that no two computers have the same ip address, as that could foul things up.

Once you have the network setup properly, then you can on to setup samba.

---

### Post by emarkay on 2010-03-10
> **cariboo907 said:**
> My comment was most directly pointed to emarkay, as he seems to be the one doing most of the complaining.


Aw come on I am not complaining, this is a legit issue that is shared by more than a few users.  Why is it that I have to be acused of "complaining" just because I have a multi-year, multi release, multi PC networking issue that I have actively, more than once tried to work directly with the developers and got nowhere.  :( 

> **cariboo907 said:**
> With windows there is not much to do except setup the shares properly, and make sure all the computers on the network are in the same workgroup. Depending on what version, Home/Pro you are using, the workgroup is set to MSHOME in the home versions and WORKGROUP in the pro versions. Another thing I do is assign the computers names, so they are easier to find than the default names that Windows assigns the system.

That's basic and obvious, done already.

> **cariboo907 said:**
> The next thing you need to make sure of is that all the computers on the network have an ip address that is in the same netblock. Using a router for DHCP solves that problem for most networks, but if you have set any static ip addresses make sure that are also in the same netblock, for instances if you router assigns addresses in the 192.168.1.1 - 192.168.1.100 range, static ip address should be in the 192.168.1.101 - 192.168.1.254 range. One other thing to do is make sure that no two computers have the same ip address, as that could foul things up. Once you have the network setup properly, then you can on to setup samba.

My secondary issue, and one as a professional Tech Writer and Multimedia Consultant, is the sad state of documentation; again for a core OS feature, it shouldn't be this difficult to configure - and to document the steps needed to do to accomplish.

Again I offered my assistance, but yea, I'm just complaining...  [insert baffled and disheartened smiley]

---

### Post by cariboo on 2010-03-10
IF you are willing to help out with documentation, have a look [here]("https://wiki.ubuntu.com/DocumentationTeam").

I know this [how to]("http://ubuntuforums.org/showthread.php?t=202605") is being rewritten, but I used it to get samba working after I'd be away from things for a couple of years, I found it quite helpful.

---

### Post by VastOne on 2010-03-10
> **cariboo907 said:**
> 

My comment was most directly pointed to emarkay, as he seems to be the one doing most of the complaining.


IF you are willing to help out with documentation, have a look [here]("https://wiki.ubuntu.com/DocumentationTeam").

I know this [how to]("http://ubuntuforums.org/showthread.php?t=202605") is being rewritten, but I used it to get samba working after I'd be away from things for a couple of years, I found it quite helpful.


Maybe it's just me, but you seem to be a bit harsh with your statements to emarkay.  It seems to me that he is trying every way he can to get help, help with the docs and offer all he can to this community...

Thought that was what it was all about...

---

### Post by timosha on 2010-03-11
> **cariboo907 said:**
> 

Once you have the network setup properly, then you can on to setup samba.

Thanks for the lessons, but the network is setup properly. Unfortunately, your post does not explain why gvfsd-smd-browse goes in an endless loop when opening a samba share and uses 100% CPU until it is killed manually.Ditto for gvfsd-network and gvfs-smb. Please reveal to us how you resolved that problem.

---

### Post by whoop on 2010-03-11
> **timosha said:**
> Thanks for the lessons, but the network is setup properly. Unfortunately, your post does not explain why gvfsd-smd-browse goes in an endless loop when opening a samba share and uses 100% CPU until it is killed manually.Ditto for gvfsd-network and gvfs-smb. Please reveal to us how you resolved that problem.

Yep it's gvfsd-smb-brows at 100% cpu usage for me, I even tried upgrading a working 9.10 desktop to 10.04 and it got the same problem. Could even be that samba **is** working for us but we never get there cause gvfsd-smb-brows is hogging all resources.

---

### Post by timosha on 2010-03-11
It is not really a Samba problem. It is a Gnome problem, more specific a problem with gnome-keyring.

This problem can be easily reproduced. On a NAS or a server create three shared folders, one without password protection and two with password protection. In Seahorse delete all existing keys for those shared folders, if they already exist.

1) Open the share without password protection. Samba will open it without problems;
2) Open one of the password protected shares. Seahorse will ask for a username and password. Enter both and Samba will open the share;
3) Now open the second password protected share. A message will pop up and nvfsd-smb-browse and nvfsd-smb go in an endless loop with a 100% CPU load;

4) Kill the nvfsd-smb processes;
5) Delete the key in Seahorse;
6) Go to step 3 and you'll see that the misery starts again;

I can reproduce this behaviour on a Thinkpad R50e, R51 and R52. And on a HP Pavillion  and dx2400 miniATX.

---

### Post by tekstr1der on 2010-03-11
> **timosha said:**
> It is not really a Samba problem. It is a Gnome problem, more specific a problem with gnome-keyring.

This problem can be easily reproduced. On a NAS or a server create three shared folders, one without password protection and two with password protection. In Seahorse delete all existing keys for those shared folders, if they already exist.

1) Open the share without password protection. Samba will open it without problems;
2) Open one of the password protected shares. Seahorse will ask for a username and password. Enter both and Samba will open the share;
3) Now open the second password protected share. A message will pop up and nvfsd-smb-browse and nvfsd-smb go in an endless loop with a 100% CPU load;

4) Kill the nvfsd-smb processes;
5) Delete the key in Seahorse;
6) Go to step 3 and you'll see that the misery starts again;

Okay, now that you've determined repeatable STR for this issue, have you filed a bug against the package in question?

---

### Post by timosha on 2010-03-11
> **tekstr1der said:**
> Okay, now that you've determined repeatable STR for this issue, have you filed a bug against the package in question?

See post #3.

---

### Post by whoop on 2010-03-11
> **timosha said:**
> It is not really a Samba problem. It is a Gnome problem, more specific a problem with gnome-keyring.

This problem can be easily reproduced. On a NAS or a server create three shared folders, one without password protection and two with password protection. In Seahorse delete all existing keys for those shared folders, if they already exist.

1) Open the share without password protection. Samba will open it without problems;
2) Open one of the password protected shares. Seahorse will ask for a username and password. Enter both and Samba will open the share;
3) Now open the second password protected share. A message will pop up and nvfsd-smb-browse and nvfsd-smb go in an endless loop with a 100% CPU load;

4) Kill the nvfsd-smb processes;
5) Delete the key in Seahorse;
6) Go to step 3 and you'll see that the misery starts again;

I can reproduce this behaviour on a Thinkpad R50e, R51 and R52. And on a HP Pavillion  and dx2400 miniATX.

But I can't even get to a server, as soon as I enter "Windows Network" my cpu goes crazy and nothing happens, I haven't even selected a server let alone a share.

I can't even go to location: "smb:///"

---

### Post by emarkay on 2010-03-11
Joined the Doc team...  

Just am befuddled at the trouble something inherently essential to modern computing is in this OS...   I really can't blame Ubuntu, as I am sure it's some config issue, but, well, then, maybe I am spoiled; I was amazed at Win95 Plug-and-Play for the hardware, and all those Wizards - lame, but effective...

We need something like that here; no, not the lameness, but the enthusiasm.
(sorry, in a lamenting mood...)

---

### Post by cariboo on 2010-03-11
It looks like since the last samba update, connecting from nautilus just doesn't work, I'm trying to determine where the problem lies.

**Edit:** Tonight I can browse shares from nautilus, the only thing I did since yesterday is reboot. The one thing I did have to do was enter the workgroup in lower case, as I don't use the default one. Cpu usage was it's normal 2-3% even while running gnome-shell.

---

### Post by dino99 on 2010-03-12
i'm glancing about:

- resolv.conf only have 192.168.1.1 (which is my router)
- can't find network tray icon (usefull to know how network is)

---

### Post by ybytyruzu on 2010-03-12
Hi, I installed Dolphin and whit it I can browse all my windows network places without problem, but with Nautilus I have the same problems that's mentioned here

---

### Post by cariboo on 2010-03-12
It seems this bug has been sent upstream to the gnome devs see bug #[611584]("https://bugzilla.gnome.org/show_bug.cgi?id=611584")

---

