---
title: "I WAS HACKED WHILE UPGRADING TO 20.04!  Suggestions needed!"
date: 2021-02-13
forum: Installation &amp; Upgrades
---

### Post by archaeometrist on 2021-02-13
**I just discovered that someone had hacked into my system, and it all started after (or during) the upgrade! ** I was able to stop the hacking (yanked the Ethernet cable, changed my password, then reconnected and reinstalled my firewall).  I then used RKhunter to look for problems.  According to RKhunter, there was one file under usr/bin that had been replaced with a larger text file that could be run.  I immediately moved that into quarantine.  RKhunter also found that Gnome Flashback was too big - 256mb vs 1mb.  I'm not sure if that's valid or not.

I actually watched as the person tried to move things around and then started trying to run different programs - and I did have files deleted (like my firewall).  I have ClamTK (it seems to be a scanner only),apparmor is in my system (although I don't know how to use it), and I will be changing the rest of my passwords.  I scanned regularly for viruses while running 18.04, btw.

Does anyone have suggestions for what to do next?  I haven't run ClamTK on my system since the hack, although I'm getting ready to do so.  I don't know if it will find anything - and I have had instances where it 'found' viruses in software that was clean (like text files I had made).

The problems started either during or right after the upgrade from 18.04 (which had some different problems that didn't point to hacking - and the upgrade fixed those issues).  The hacker was mainly acting in the background, until when I caught that person doing stuff involving the desktop (and deleting files).

(I'd call the police about it, but don't have proof AND the local "Finest", the last time we had someone hack us (got into our router, turn on wifi, turned off encryption, and was downloading huge amounts of data while shutting us out - and then our software detected an attempt to get through our system firewalls) the police said there was nothing they could do, unless we could show that the hacker was doing something like downloading kiddy prn.  They saw it happening with their own eyes, and i used "wifi radar" to show them where it came from (a 20 something that had proved to be a real problem!).

(1) Please be aware that hacking happened during (or within minutes after) the upgrade. 
(2) I could use advice on what to do to prevent more hacking.  I do the updates right away and am careful where I go on the internet.
(3) Could someone suggest software that would help to keep hackers and so on at bay?

Thanks!

Bob

---

### Post by QIII on 2021-02-13
How are you connected to the internet?  Did the intruder compromise your router/gateway?

---

### Post by archaeometrist on 2021-02-14
That I don't know yet.  I've been trying to find problems in my system - something is off because the firewall on my computer was turned off again (it's supposed to stay on).

I did find a bitcoin miner via rkhunter.  It's in quarantine.  I'm not sure how bad it is beyond that.  I've been doing a full scan of my files (took hours), nothing found beyond the few.  Right after I'd finished the upgrade, I had a weird thing happen - a warning of a memory overflow (or something like that) - that was before I started putting back in even basic programs.

---

### Post by archaeometrist on 2021-02-14
Correction - I believe it was ClamTK that found it.

---

### Post by archaeometrist on 2021-02-14
OK, more info.  I have Global Protect installed (from my school - also my employer).  I had a pop-up which stated "PanGPUI assert failure: ***stack smashing detected***:Terminated.  Funny thing is that I thought I saw a pop-up like this before - but that was _before_ I had globalprotect installed.  I've removed Global Protect (at least I think so).  I don't know if that has anything more to do with it, but after I saw the pop-up I tried to remove GlobalProtect via their instructions, and the system returned that it was NOT installed.  I found a .sh file for uninstalling and that may have done it, I don't know - the text said that it was uninstalled (and user removed).  (I got the software from our IT department.)   

Hope this helps - I've wasted a week and a few days almost nonstop trying to figure out why I was having so much trouble with 20.04!

---

### Post by archaeometrist on 2021-02-14
(I should add that I JUST had the pop-up a few minutes ago.)

---

### Post by Impavidus on 2021-02-14
If a hacker gained access to your computer, the only sure way to get rid of it is to nuke your system and make a fresh install. Format your hard drive, only keep documents known to be clean.

---

### Post by archaeometrist on 2021-02-14
It took me two days to install everything, and I have literally thousands of documents that I keep (I'm a doctoral candidate and work as a part-time researcher).  I don't HAVE two more days to go through and wipe-and-reinstall.  I'll lose my job, and that will destroy any hope for a future.  Therefore, I need a REAL solution, one that works.

Let me put it this way - just getting the documents related to my dissertation research re-uploaded (with a fast backup drive) took three hours (that does include data and pictures).  My latest (this month's) project  for work involves over 400Mb of PDF files that I downloaded and have to read (official reports).  I'm not going to start over.  I CAN'T.

There MUST be a different solution - and also this thread was a heads-up that something strange happened during (or just after) installation of 20.04.  The symptoms started BEFORE I started uploading my files - and I didn't have any evidence of hacking before.

---

### Post by mikewhatever on 2021-02-14
There is no way we can know what happened without you providing detailed info, which you seem to have no time for.

I happen to know a good solution for you, it's <sudo poweroff>.

---

### Post by archaeometrist on 2021-02-14
I don't need snide and abusive comments either.  If you can't help (or don't have reasonable suggestions), keep the comments to yourself.  I didn't come here to be abused!

I don't know WHAT information that might be needed - I'm doing the best I can!  (I'm not a newbie, but I'm not a guru or OS enthusiast either.  A computer is a tool, plain and simple - nothing more.  I use Ubuntu because of all the problems I've had with Microsoft - starting BEFORE Windows.)

---

### Post by T6&amp;sfpER35% on 2021-02-14
timeshift maybe ? to restore your system to a state it was in before the upgrade ?
not sure what happens to timeshift during a upgrade , might be worth a look at.

---

### Post by archaeometrist on 2021-02-14
I'll look into that.  This is the first time I've heard of timeshift - and I don't know if the system was backed up or not (I deleted everything and started from a DVD I burned with 20.04).

Thanks for the reply and suggestion!

---

### Post by QIII on 2021-02-14
> **archaeometrist said:**
> I don't need snide and abusive comments either.  If you can't help (or don't have reasonable suggestions), keep the comments to yourself.  I didn't come here to be abused!

Nor are you being abused.  For now, your machine must stay off.  If you are compromised, then a full re-install is the only safe option.  I am sorry, but that is the reality of the situation.  If you did not backup your important files, you may simply be out of luck.  There is no way to know if those files have been tainted.  

You may have learned a very hard lesson.

I will repeat my initial question and I hope you will find it in your heart to answer this time:  How are you connected to the internet and was your router/gateway compromised?

At this point, all other questions are academic.  Until you have a secure connection, NOTHING you do will be safe.

---

### Post by T6&amp;sfpER35% on 2021-02-14
where did you get this ISO for 20.04? the ISO image could have been compromised. 
i suggest downloading from [here](https://ubuntu.com/download/desktop)

---

### Post by T6&amp;sfpER35% on 2021-02-14
> [COLOR=#000000]and was your router/gateway compromised?[/COLOR]
how does one check / know that ?

---

### Post by Impavidus on 2021-02-14
> **QIII said:**
> If you are compromised, then a full re-install is the only safe option.Or a restore of a full system backup created before the hack happened, but most people only backup their documents or home directory, not the entire system. Precisely because it's so easy to reinstall.

---

### Post by QIII on 2021-02-14
> **Impavidus said:**
> Or a restore of a full system backup created before the hack happened, but most people only backup their documents or home directory, not the entire system. Precisely because it's so easy to reinstall.

Based on the user's discussion to this point, I think it safe to proceed on the assumption that no backups occurred.

---

### Post by QIII on 2021-02-14
> **3nd said:**
> how does one check / know that ?

As with nearly any machine:

Remote management is enabled; you have used a weak password; your login credentials fail; you see an unknown IP address on your network;  odd redirection to unexpected websites; ransomware messages; router settings have been altered ...

---

### Post by archaeometrist on 2021-02-14
Believe me when I say this - I am very careful with my system. ** I HAVE NO CHOICE BUT TO PUT MY DATA BACK IN. ** Yes, I do have copies BUT I WILL NOT THROW AWAY ANYTHING.  Most of it is on a backup drive which stays off my system unless I am accessing it.  Oh... I'll tell you what.  I'll do that - if you'll pay me a year's worth of wages (at a decent level, no more minimum wage) and get the school to add that extra year to my deadline, because it would take that long (at least) to 're-do' everything, although I backed most of it up (some on archival Blue-ray disks, but some also on DVD, but most on the backup drive).  Under 18.04, I had the system locked down, because of my work AND because of some of the data I handle.  The hacker got in AFTER the upgrade to 20.04, but before I started putting my data back in.


**I only know one thing I could (and should) have done when I first installed 20.04 - see if I could set up different accounts - one just for Firefox and Tbird (internet), one just for work, a generic higher one (able to use sudo), and then root.  My passwords are quite strong - most of the critical ones are 20 to 40 characters long with an appropriate mix.  Thus, with the exception of the different accounts - tell me, what else could I do (especially since I have limited resources)?  **

Here's some more information.  I downloaded the ISO from Ubuntu (the official site) - and checked to make sure it was the proper site.  After it was installed, I installed (from the official repositories) the firewall and setup for it.  Then ClamTK.  (I scanned my 18.04 files I'd put on the backup before starting the switch, btw.)  Then Gnome Flashback.  Then I installed Remmina.  Then I installed (from my school's IT department security section) Global Protect - it was after that was put in that I started seeing some minor strange stuff.  THEN I started copying the important files back to the system.  90% or more of them are pdfs, or Write documents, or spreadsheets of data (which were scanned with ClamTK during 18.04).

Then the weirdness got worse - I was installing software FROM THE OFFICIAL REPOSITORIES and noticed stuff being missing (like the Desktop icon under "places").  I started seeking help, thinking it was some sort of bug.  It was after that when I actually saw that it was a hacker (and found that the firewall had been uninstalled).  That's when I submitted this request for help.

Re-installing may cost me my job (and I'm way behind schedule on my dissertation research).  I really hope that someone has a better idea.  I'm not some comfortable person with lots of money and who likes to play with resources - I can use Linux and do some command-line work, but have to search for needed changes.  I spend nearly all of my time studying and learning - my job entails reading formal scientific reports (usually pdf) downloaded from government sites, and gleaning metadata from them. 95-98% of the files I have to put back in are in PDF form or jpg.  At least a couple of % are spreadsheets of data **I** generated.  Dismissing my situation as a "hard lesson" does not match the facts.  There is nothing to be learned here - the only difference is that maybe I could go the multiple accounts route (which I'd considered but because of the care I took before, thought that might not be necessary).

---

### Post by QIII on 2021-02-14
Not careful enough, it would seem.  This is less likely the result of lack of effort on your part than simply not understanding the danger and processes for securing yourself.  This is not an attack on your person or your intelligence, but a fact of life in this technical context.  This sort of thing happens to the most knowledgeable and careful among us.  Millions of personal records are compromised by companies employing hundreds to techies whose job it is to avoid such.  Billions of dollars are lost by others.

Now, again:  How do you connect to the internet?  Has your router/gateway been compromised?  If you will please provide that information, we might begin to tell you how you got into this situation and how to get out.  There is likely nothing at all we can do to help if the back door is left open and somebody knows about it.

Hackers DO NOT CARE at all how much work you have invested in what you have on your machine.  They do not care at all about the fact that you might have lost a job.  They do not care that you are a PhD candidate.  They have no emotional attachment to you at all.  An emotional appeal to us is heartrending, but ultimately will likely come to naught if we can't manage to help you keep the bad actors out.

A couple of other items 

> Then I installed Remmina. Then I installed (from my school's IT department security section) Global Protect -

How did you secure Remmina?  Have you reported the incident to your school's IT department?  Is it possible that they, too, were attacked?

---

### Post by grahammechanical on 2021-02-14
I am sure that you know more about this than I do and have tried many things that I would not have known about. Let me review your situation. Need to use your computer for work and to finish a dissertation. You are up against a skilful hacker who knows his stuff. How do you proceed from here?

You must limit your use of the internet. You cannot use that operating system. Can you use Ubuntu in a live session and work from that? When you go online for your very good reasons can you do so from the Ubuntu live session and with the hard drive disconnected? Can you do without applications that you at present consider essential? Can you afford a new hard drive?

I am trying to think of things that will let you continue working as there does not seem to be a quick fix. The hard drive and OS are compromised. I think that someone is targetting you and I do not think it is some hacker making random attempts to get access to a stranger's system. I know little about hackers but from what I have heard they take pains not to reveal that they have accessed the machine. Unless their purpose is to extort payment by locking the whole system down.

I assume that you know enough from past experience to do a factory reset of the router and to then change router labels and passwords. You do not have time to sanitize the hard drive so you will have to do it over time. Meanwhile, you need a way to continue working that limits the risk. I would not eliminate as a suspect anyone in your school's IT department either.

You have my sympathies.
Regards

---

### Post by archaeometrist on 2021-02-14
Uggh.  Router may be compromised.  I ran into a problem as soon as I  went to it (self-signed certificate).  I'd not encountered that before.   I don't know if there is a way around it or not - but I need to warn my  wife.  She works from home too.  I could try to log in, but I'm feeling  really cautious.

We do have a very talented hacker in our area - previous problems  (several years ago) were caused by the jackass.  The guy (we have a  really good idea of who it was) would literally hack into our  router/modem through cable, turn on the wireless and turn off  protection, and would either be downloading huge files or more likely -  playing some sort of network-intensive game.  He'd shut down our  internet by hogging the bandwidth.  (Local "Finest" said they could do  nothing unless we could show that he was downloading kiddie porn or  committing some other crime - their hands were tied and it put the onus  on us.  Our ISP provided us a new router/modem combination, which is  supposed to be very secure (a 'special one').  I'd not seen any  indications of being hacked like that - until this latest headache.)

I'm hoping that the backup drive wasn't compromised - because of the  stuff that's on it, I doubt it (and I think it could be scanned once I  get this system secure)!  I only used it as a source for all of the  necessary files.

By the way - thanks for letting me know more what information you need.   I may be quite experienced in some things, but this is way over my  head.  I can figure out and fix more 'ordinary' problems as a general  rule.

I installed Remmina from one of the initial installation packages that  were present just after the installation DVD was removed and the  software restarted.  There are at least a couple - Software (Not much  good), and Packages.  Also "Software Install" (does nothing) was in the  System Tools folder.  I did install Synaptic Package Manager - I prefer  that at times, because things will be found by it that don't show  elsewhere and I've been able to use that to solve problems.  (I also  have used apt-get install - with only the official sources enabled.)  As  far as my school's IT department, I shot off an email to one of the  people there who knows a bit about linux.  Most are cookbook Windows  only types.  The guy I know is pretty good.

---

### Post by archaeometrist on 2021-02-14
> **grahammechanical said:**
> I am sure that you know more about this than I do and have tried many things that I would not have known about. Let me review your situation. Need to use your computer for work and to finish a dissertation. You are up against a skilful hacker who knows his stuff. How do you proceed from here?

You must limit your use of the internet. You cannot use that operating system. Can you use Ubuntu in a live session and work from that? When you go online for your very good reasons can you do so from the Ubuntu live session and with the hard drive disconnected? Can you do without applications that you at present consider essential? Can you afford a new hard drive?

I am trying to think of things that will let you continue working as there does not seem to be a quick fix. The hard drive and OS are compromised. I think that someone is targetting you and I do not think it is some hacker making random attempts to get access to a stranger's system. I know little about hackers but from what I have heard they take pains not to reveal that they have accessed the machine. Unless their purpose is to extort payment by locking the whole system down.

I assume that you know enough from past experience to do a factory reset of the router and to then change router labels and passwords. You do not have time to sanitize the hard drive so you will have to do it over time. Meanwhile, you need a way to continue working that limits the risk. I would not eliminate as a suspect anyone in your school's IT department either.

You have my sympathies.
Regards

Thanks!  I do have some pretty nasty enemies - almost 11 years ago they torched my electronics workshop/home laboratory for writing a letter to the editor they didn't like.  They also threatened my elderly parents and ordered them to 'shut him up'.  They also poisoned several of our kitties over a two or three year period and have caused us untold grief.

I guess I can't say who they were, but I think I can say this - they've been stalking us on and off for decades - and I did get a guy put in jail for internet stalking about 15 years ago.  I would not be surprised at learning I'm being targeted.  I just wish I could prove it.

Your reply was encouraging.

---

### Post by QIII on 2021-02-14
Since I have no reason to doubt the veracity of what you have told us, I would suggest that you stop using your possibly compromised machine and ask your wife to do the same.

You would do well to contact the UF via internet access gained at some other location, such as a trusted friend's home.  Or seek out a local Linux Users Group (LUG) for assistance.  There are jerks in every community, but there are many more helpful people.

If someone that vicious is indeed intent on such treachery, they'll already have access to any compromised hardware to just watch what is going on.

As I said, they don't care about you.  They won't decide to play nice just because you are asking us for help.

---

### Post by archaeometrist on 2021-02-14
I learned decades ago how evil and cruel they are, and I never expected them to play nice - what I did expect is suggestions on how to deal with this - how to fight the person off and keep him or her out.   Dozens of death threats and worse (Yeah, I know, people probably won't believe me) taught me long ago how dangerous they were... but I'd taken more than the usual steps to protect us.  Like you said - even corporations with IT departments get hacked.  (Most of the hacking I've heard about happened because someone opened phishing emails, or management either underfunded the department or worse - told them to cut corners.)  I do wish I could get proof of what I strongly suspect is going on - but that's not likely to happen.  I'm only too aware of reality to have much hope.

Yes, the router is compromised.  Resetting it (while NOT connected to the internet) does no good - the default login doesn't work in any case (when our ISP was bought out, the new company replaced a high security router with one that turns out to have the most hack-able default login possible (I'd forgotten that this was not the high security router).  We've changed passwords a few times on it (strong passwords according to the indicator) according to our written records, but it was still hacked.  The only way in or out besides the modem is wireless - that is one point of entry I didn't deal with (except to have the latest type of available encryption on it and a strong password).  We both have to get on to change a couple of things and let some people know - the only people in this area that I'd trust have probably already gone to bed.  I do have an older Ubuntu laptop, but I don't want that compromised.  

I don't know about the modem, but I am contacting our ISP asap (it's their router).  I'm using the computer just to let people know what is going on.  I'll try to check in here and see if anyone has ideas that could help.  It does look like I have to re-install everything.  (SIGH!)  (I just hope that the Ubuntu iso wasn't compromised from the beginning!)

I'll try to check in one more time tonight to see if anyone else has an idea or suggestion.  (Laugh!)  I actually long for the good ole days when hacking and viruses were rare!  I'm going to generally keep the ethernet cable disconnected until I'm relatively confident we've got it dealt with.

---

### Post by archaeometrist on 2021-02-14
Final comment for now - I'm going to take this computer offline and try a re-install of 20.04 and my files (mainly those stored on archival Blu-Ray disks before I upgraded).  I'm not sure what will be on the Ubuntu DVD as far as software, but we'll see.  I've got an old laptop (16.04) and if I can find the 18.04 update disk, I'm going to get it updated that far - so if we can get the router and modem straightened out, then the laptop might take care of some of the work in the meantime.  I do hope that ClamTK (or something similar) can find anything bad and prevent re-infection.

That's the best I can do.  I'll give a report when done on this thread - there may be information there which would be useful for others (to fight off this sort of nonsense). In the meantime, I hope we can somehow track down who did this... it would be nice to see some justice done!

---

### Post by DuckHook on 2021-02-14
While others have shown forbearance, my role must now be governed by an objective assessment of the facts.

You have steadily graduated from claims of hacking to intensifying claims of heavy persecution. I am not in any position to judge your claims and, in any case, they are irrelevant to the technical issue at hand.

However, what **is** relevant is your absolute conviction that you have been completely compromised while simultaneously insisting on canvassing for solutions through that very completely compromised medium. This is so foolish as to be mind boggling. Moreover, rather than follow the excellent advice already given, you imperiously demand solutions that do not exist and therefore amount to nothing other than magic.

You even announce your intention to revisit this thread yet again through the very router and other hardware that you have every reason to thoroughly distrust. These are neither reasonable nor responsible actions.

If you post again without first having taken the simple steps already laid out by at least half a dozen forum members, I will be forced to conclude that you have no serious intent, are only out to waste everyone's time and will summarily close this thread.

Please govern yourself accordingly.

---

### Post by Topsiho on 2021-02-15
If you are what you say you are, and if has happened to you what you say has happened to you, I don't get that you are seeking advice here on this forum from people you don't know a thing about. Whose qualifications you don't know.
I don't get that you are not seeking advice from a systems administrator of your university.
The kind of problem that you describe is quite alien to the experiences of most of us. From what site did you do or get the upgrade? In the first place. Was the problem already existent on your previous installation? Was it a Linux system?

Impavidus gave you a very sound advice, not being aware of the seriousness of your problem. If he was he would have told you to get professional advice.

Good luck with getting rid of your problem, with professional help

Topsiho

---

### Post by kansasnoob on 2021-02-15
> **archaeometrist said:**
> Final comment for now - I'm going to take this computer offline and try a re-install of 20.04 and my files (mainly those stored on archival Blu-Ray disks before I upgraded).  I'm not sure what will be on the Ubuntu DVD as far as software, but we'll see.  I've got an old laptop (16.04) and if I can find the 18.04 update disk, I'm going to get it updated that far - so if we can get the router and modem straightened out, then the laptop might take care of some of the work in the meantime.  I do hope that ClamTK (or something similar) can find anything bad and prevent re-infection.

That's the best I can do.  I'll give a report when done on this thread - there may be information there which would be useful for others (to fight off this sort of nonsense). In the meantime, I hope we can somehow track down who did this... it would be nice to see some justice done!

I would absolutely NOT upgrade that 16.04 PC until you have any other issue resolved! Ubuntu 16.04 is still supported until April, at which time you could even sign up for the free ESM:

[https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

Also I thought they had already disabled the "upgrade via Live DVD" option in 18.04. If not it's still quite a poor upgrade option - very unreliable! If the same method was used for upgrading the effected machine that well could have led to your problems with the flashback session that you spoke of in a prior thread.

Bottom line: Don't take on another challenge until the prior one is sorted out! If you have a 16.04 PC that's working well just apply normal updates and use it until things are sorted out. Maybe a broken upgrade on the "effected" machine has just given the appearance of being hacked? I'm not saying that is what's going on, just raising the possibility.

---

### Post by kansasnoob on 2021-02-15
BTW trying to "upgrade out of a problem" almost never works. I speak from personal experience. If it's broke an upgrade will usually only make matters worse!

---

### Post by DuckHook on 2021-02-15
The staff have decided to close this thread.

In your attempts to help, you have all demonstrated admirable proficiency, patience and kindness, and are a credit to our community. Thank you all for your continued contributions.

---

