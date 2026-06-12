---
title: "[SOLVED] Easy Antivirus?"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by gobbles414 on 2007-07-26
Hi all,

After posting a couple of threads asking for help with linux antivirus software that can scan my emails, I still have not made any progress. So, I have decided to seek as simple an antivirus solution as possible for my Feisty box. Here is my wish list:

* easy to install via synaptic or deb package (or rpm via alien conversion tool)
* can update and scan from a GUI (neither of the clam GUIs provided in ubuntu have worked for me)
* scans archives and hidden files
* can manually scan my thunderbird emails... That is, I want to be able to tell the scanner to scan the .mozilla-thunderbird directory. My inbox is represented by the file Inbox.msf. So, I need a scanner that can scan .msf files.

I appreciate all of your help in advance.

---

### Post by ajgreeny on 2007-07-26
I'm surprised either klamav or clamtk don't work on your machine.  What are the problems with them?  They work OK usually without problem so I just wonder what is different about your setup.  Have you tried the terminal use of clamscan?  It's so easy to use I sometimes wonder why people need the GUIs.

---

### Post by ThrobbingBrain66 on 2007-07-26
[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

scroll down a little bit for the AVG instructions.

---

### Post by Voynix on 2007-07-26
What about Avast? I followed [Ubuntu Geek's instructions]("http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html") and [yopnono's]("http://ubuntuforums.org/showthread.php?t=229128&highlight=avast") thread: 

1. **Downloa**d the deb package from [Avast]("http://avast.com/eng/download-avast-for-linux-edition.html") and [B]install
2.[/B] Get the** Registration key** from [here]("http://avast.com/eng/home-registration.php")
3. Set the icon for the [B]menu: (Applications, Accessories)
[/B]```
cd /usr/lib/avast4workstation/share/avast/desktop
sudo ./install-desktop-entries.sh install
```4. Use **GTK2 interface**
```
cd /usr/lib/avast4workstation
sudo rm -rf lib-x11/
sudo rm -rf lib-gtk2/

```Avast (although proprietary) will be a good solution.

---

### Post by gobbles414 on 2007-07-27
Hi all,

Thanks for replying to my post. As has been well documented in the Ubuntu Forums, the clamtk package cannot find the virus definitions database, so that is not an option. The avscan package for clam gets stuck in an endless loop when recursively scanning the entire disk (*/*). Klamav looks like it is a great program for Kubuntu, but it doesn't integrate very well in the gnome environment -- at least on my system. I have already tried AVG. Please see one of my previous threads here ([http://ubuntuforums.org/showthread.php?t=467797](http://ubuntuforums.org/showthread.php?t=467797)). I believe that page 4 has most of the information on my AVG results. I haven't tried Panda yet because the installation procedure looks tricky, plus it costs money to use.

Per Voynix's instructions, I have installed Avast from the official deb package. The procedure worked flawlessly on my system, as did the definitions update. But the scan ran into a few problems. I am running the scanner with the *gksudo avastgui* command as a normal application. I ran a thorough scan of the */* directory with test archives enabled. Chest and log file sizes were set to 0 (no limit). The actual log of failed files during the scan is over 200 pages long! So obviously I cannot post all of it here. Nevertheless, I have included several good examples in the list below. I would say that 90% or more of the failures took place in the */sys* directory.

2007-07-27 13:22:41	Error while scanning '/lib/terminfo/v/vt52/#': ARC archive is corrupted.
2007-07-27 13:22:59	Error while scanning '/proc/acpi/event': Device or resource busy.
2007-07-27 14:27:59	Error while scanning '/dev/bus/usb/.usbfs/004/002': No such device.
2007-07-27 14:27:59	Error while scanning '/sys/block/sr0/queue/scheduler': No such device.
2007-07-27 14:27:59	Error while scanning '/sys/block/sr0/uevent': Permission denied.

I will be testing the Avast scanner with Eicar virus test files later today, and I hope to report back on those results soon. In the meantime, **could someone tell me why so many of the files failed to be scanned by Avast?** Thanks again for the help!:)

---

### Post by Gremlinzzz on 2007-07-27
Don't forget to scan for rootkits. Install chkrootkit in synaptic package manager.
to use just type  sudo chkrootkit in terminal
:guitar:

---

### Post by gobbles414 on 2007-07-29
Hi all,

As promised, I am reporting back with my results for the Eicar virus test files. On the good side, both the text version and the zip version of the test virus were detected by Avast when they were placed on my desktop.

On the minus side, **I could not get Avast to detect the virus files when they were in my Thunderbird inbox**. I had  pasted the text from the virus file into the body of the email. In addition to that, I also added the zip file to the email as an attachment. As my email provider does not allow test virus files to be sent over their servers, I saved my message as a draft and then moved it into my inbox.

I could always switch from Thunderbird to my email provider's webmail service, which offers automatic virus scanning for both sending and receiving. But for privacy and ease-of-use reasons, I would prefer to be able to scan for viruses in Thunderbird. I'd also like to keep using Avast if possible. It has worked the best of all the antivirus programs that I have tried. If needed, I am willing to pay a small fee for an antivirus solution that meets my needs. **Any more ideas...?**

P.S. I have installed and run chkrootkit. I watched as the scan was taking place, and all results looked good. However, the terminal window closed as soon as the scan had completed. So, it was impossible for me to recheck the results.

---

### Post by gobbles414 on 2007-07-29
Hi all,

Just a clarification... I did not try to integrate Avast with Thunderbird for always-on scanning. I did a manual scan of the .mozilla-thunderbird directory with the gksudo avastgui command. Thorough scanning and test archives were both enabled. I know for a fact that .mozilla-thunderbird is the correct directory to scan because I have been able to backup all of my messages by copying files from that location -- thus all messages are stored somewhere in that folder.

---

### Post by gobbles414 on 2007-07-30
bump:popcorn:

---

### Post by gobbles414 on 2007-08-06
Hi all,

I'm still hoping that somebody will help me with my antivirus problems. I am working more-and-more with colleagues who are on Windows and I need to make sure that I don't infect them (it could mean lots of lost $ for me if that ever happened). It won't matter to these people that Linux is immune to viruses. What will matter to them is that I have sent an infected file to them.

I do not mind installing a kernel module if necessary. I'll just need some guidance with the installation procedure -- I've never modified a Linux kernel before.

Again, Avast is by far the most user friendly antivirus solution I have found. I just have a few wrinkles to iron out. I haven't been able to try Panda because they ask for a lot of personal information that I am not willing to give them on their download form.

**Will someone please help me?** Otherwise I'll have to start yet another thread in another part of the forums (yuck!).

---

### Post by Gremlinzzz on 2007-08-06
Don't forget to check for madcow
sudo apt-get moo
:guitar:

---

### Post by gobbles414 on 2007-08-07
Hi all,

Yes, the text-based picture of Moo is hilarious! But, I'm still waiting for some more antivirus help.

---

### Post by gobbles414 on 2007-08-08
bump

---

### Post by gobbles414 on 2007-08-11
Hi all,

I've managed to find a workable solution to my antivirus problems! Here is what I did to scan my emails:

(1) Use Evolution instead of Thunderbird. :-({|=
(2) Place virus test text in a draft message and attach a compressed test file (.zip). Drag the message to the inbox.
(3) Use Avast to scan the hidden .evolution folder in the home directory.
(*) Running the scan as gksudo requires one to manually navigate to one's real home directory (Avast in gksudo thinks that root is its home).
(4) The scan failed to delete the virus text in the subject field, or the contaminated message itself. But **it did sanitize the message body and delete the offending attachment**. =D>
(*) I assume that the subject field was ignored because it cannot execute any code?

So, I can count on Avast to do a decent job scanning my Evolution inbox. That is a big leap forward for me. Now, If I can only get Avast to complete a full disk scan without the 200 pages worth of failures...

---

### Post by DavidTangye on 2007-08-12
Well judging by the lack of help you have got on this issue, I guess we can assume that there are not very many around here interested and able to advise on viruses in Linux. As you alluded to before, virus = Windows, not Linux. So no-one here is very concerned with them. You dont want to pass any on to customers. I know in my case my attitude is this:

Viruses are a 'feature' :-) of Windows.
If I unknowingly receive one from the Windows world, and forward it back into that world, so what. I can't be expected to take responsibility for Gates' screwed up system. If other end-users insist on living in that world, then its their responsibility to get involved with anti-viral etc etc stuff on their machines, not mine. Everyone knows Windoze = virus. So anyone with a quarter of a brain will have anti-viral systems on their Windows machines.

---

### Post by gobbles414 on 2007-08-12
David,

Thanks for offering your thoughts. On the one hand, I totally agree with your attitude. Micro$oft users -- or companies that force their employees to use Windows -- bring viruses upon themselves by using an inherently insecure OS.

That said, Windows users do not necessarily see the world that way. It's the old argument "if he's evil, does he know that he's evil or does he think that he is righteous and good?" A customer of mine who uses Windows isn't going to go, "well, it's my fault for using Windows." More realistically, that customer will say, "that stupid Linux SOB just sent me a virus. Linux is insecure and I will never trust that gobbles414 with my business again!"

If Linux is to have any hope of gaining a decent share of the home market, we need to start "embracing and extinguishing". Just mho...

---

### Post by gobbles414 on 2007-09-18
Hi all,

I've taken a closer look at the scanning failures and noticed that they are all of hardware devices, like RAM modules. I can live with that for now. Problem solved...!

---

### Post by Gremlinzzz on 2007-09-18
[http://www.howtoforge.com/avg_antivirus_ubuntu_feisty](http://www.howtoforge.com/avg_antivirus_ubuntu_feisty)

---

### Post by info on 2007-09-18
Works on 32-bit architectures. Their downloads DO NOT work on amd64 version. I get a message that says they are incompatible. I used Avast on Windows machines, and it works very well there.

---

### Post by mendo on 2007-09-24
so what is an amd64 user to do?  do the majority of linux users go w/o a/v software?  that seems crazy to me, but i'm new to linux.

---

### Post by SpiritIsReality on 2007-09-27
howdy
mendo ...good security article, with links
[http://ubuntuforums.org/showthread.php?&t=510812](http://ubuntuforums.org/showthread.php?&t=510812)
and then there's this
[https://help.ubuntu.com/7.04/keeping-safe/C/index.html](https://help.ubuntu.com/7.04/keeping-safe/C/index.html)
[http://ubuntuforums.org/showthread.php?t=131616](http://ubuntuforums.org/showthread.php?t=131616)
and also this for servers
[https://help.ubuntu.com/7.04/server/C/](https://help.ubuntu.com/7.04/server/C/)
I have yet to do anything special about security on ubuntu desktop.
(wait's for crash of spam/virus/popups!!!!!) haha!

trails

---

### Post by bigboy_pdb on 2007-09-27
gobbles414, if avast's free Linux antivirus software seems to be problematic, you might want to try AVG's free Linux antivirus software to see how it does. I've never tried either, but maybe you'll be able to get it to work to your liking. The link for the software is as follows:
[http://free.grisoft.com/doc/downloads-products/us/frt/0?prd=afl](http://free.grisoft.com/doc/downloads-products/us/frt/0?prd=afl)

---

### Post by iansane on 2008-03-15
Someone said what about clamTK? Well it doesn't just scan anything you want it too. You have to edit the config file manually to tell it to scan big files and in archives and stuff like that. The update thing was a mess for me cause I had to figure out how to get it to update without logging in as root to do so. I don't like it. What will we do when Ubuntu is popular enough for people to start writing viruses for it? PCmag had an article that said that was the real reason it is safer but they had other articles about Ubuntu that even I as a newb new they didn't know what they were talking about so who am I to beleive? 

There's also command antivirus for linux but you have to pay for it. I'm glad to see AVG and Avast offer free AV for linux

---

