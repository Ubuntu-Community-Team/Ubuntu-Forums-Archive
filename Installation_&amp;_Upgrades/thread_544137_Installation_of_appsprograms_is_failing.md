---
title: "Installation of apps/programs is failing"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by donnie616 on 2007-09-05
I just started to put in some apps SLOWLY, this time and they are allgiving me error messages.  Synaptic FAILS!  ADD/REMOVE FAILS!  Automatix2 FAILS!.  I am not to sure but the installations may have started tfailafter I installed Automatix2. Can any one help?

2.   Is there an equivanlent to windows "System Restre" in UBUNTU?  I took some time to learn how to navigatte alittle w2hile I cannot install anything new.  I could reinstall, but then I wuold learn nothing.  

I am using a compaq D500/1.8GHZ Intel P4/768 MB ram/ on an old Envision monitor. (SCSI) 100GB NEW seagate HDD.  

Thanks, I am ready to go forwrd now.  Here is the error I just got in ADD/REMOVE, When I tried to DL Adept   .

     E: emifreq-applet: subprocess post-installation script returned error exit status 2

Everything else moves along well, response is fantastic, but I cant get any where further now. I am 2 weeks new tu UBU, please be gentle.

---

### Post by merlinus on 2007-09-06
From the ubuntu guide:

**Automatix2**

 **Warning:** *Automatix2 is a proprietary script that tries to install some software, and is known to fail and break systems. The Ubuntu community *WILL NOT* provide support for it, and strongly discourages its use. Problems caused by Automatix are often hard to track and solve, and it may result in having to reinstall your entire Ubuntu system. Ubuntu/debian developers have reviewed automatix and found it to be quite dangerous. Use Automatix at your own risk.*

---

### Post by mocoloco on 2007-09-06
I assume you've verified your internet connection is working.  It sounds like possibly your software repository sources.  Open "System -> Administration -> Software Sources".  In the first tab you can probably leave all the check boxes, but change the drop down for Download From to the opposite of what it is now (either main or your country).  Click the "Third Part Software" tab and for now uncheck everything.  Close, you'll be asked to reload source info, then if that's successful try downloading again.
If everything works, try re-enabling any third party sources you had.

---

### Post by donnie616 on 2007-09-06
ok thanks I will do what you have said, then I have to go to bed.  Ubuntu is exhausting me for now.  Aotmatix2 does not work at all.  BUT I have discovered tah update manager gives me an error msg, but works.  I tested it with some minor games.  Adept DID get through, and is functional, But  I got a script error p0rior to realizing that it had installed . so for now it looks like SOME things are installing, but not without an error message.  I wnt to uninstall Automatix.  plase tell me how.  The default updater in the upper right panel seems to work also.

Also how do i do9 a "system restore"?

---

### Post by donnie616 on 2007-09-06
Internet connect is fine. by the way. sorry about the double-post, very tired.

Thank you so much

---

### Post by mocoloco on 2007-09-06
I just noticed you're mentioning Adept.  Are you using Kubuntu, with KDE?  If tha'ts the case what I said about sources is different, I don't remember right now where you change them in Kubuntu.  In any flavor you can edit /apt/sources.list.
Merlinus makes a good point, Automatix is a third party thing.  I've used it and never had problems, but the policy is what it is for a reason, and there's apparently enough people who've been hosed by it to make the policy.  I haven't used it for a while.
I know Automatix keeps a log file, it creates a hidden folder in your home folder and puts some stuff there.  Maybe that can help you, or maybe you can use it and get better help on the Automatix forums.
[Yawn] I've got to go to bed too.

Oh, and no system-restore type function at the moment unfortunately.  Hopefully that will come in the future.

---

### Post by mattsajay on 2007-09-06
I am also having similar errors:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

this was the error displayed for the different packages i selected in synaptic:  Could not connect to localhost:4001

i have not installed automatix2 yet but was going to.

---

### Post by mattsajay on 2007-09-06
i just noticed another error: 

W: Duplicate sources.list entry [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages)

---

### Post by donnie616 on 2007-09-06
to "moco" you fixed my problem for me. I did what you said .It reloaded 0ver 1025 new whatevrs (updates?)

I will check the 2 repositories taht I unchecked and go back from main serrver and see what happens.  One of them was Automatix and the other was the reputable one, Canonical. For now, I will sta away from automatix, until I learn more.Thank you for your help

I do not have Kubuntu.  I just  gadept to see if I could.  I do not need it.  I ended up getting most of what I tried to, but with that error msg. 

I have so much to learn.  Here I go.
thank you again I will be back for sure

---

