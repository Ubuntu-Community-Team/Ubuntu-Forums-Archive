---
title: "Linux migration"
date: 2021-06-01
forum: Installation &amp; Upgrades
---

### Post by jmcguigan2 on 2021-06-01
What is the easiest way to migrate a window 10 network of 200 computers to ubuntu? Is there way to push OS to computers or installation need to be done on each computer?

---

### Post by ActionParsnip on 2021-06-01
What applications are used on the systems in the network? There isn't nearly enough information here. Can you please give details about how the systems are used......

---

### Post by scorp123 on 2021-06-02
> **jmcguigan2 said:**
>  What is the easiest way to migrate a window 10 network of 200 computers to ubuntu? 

**Been there, done that. I am not sure that you are aware what a complex task this is??**  Migrating x-100 Windows machines to a new OS is not done with *"just install a new OS. Voila, done."*  If it were that simple then even an untrained child could do this... :lolflag:   

But as it is you will need people who know what they are doing. And they will not work for free. Did you allocate enough budget for that??  Because if you didn't then this whole migration is already dead before it started.

**Also:  What about "the rest" ?? **

I imagine those Windows 10 client machines are not "alone"?? What about centralised logins such as **Active Directory**? I can't imagine that with 200 Windows machines you do not have something like Active Directory too .. because managing 100% local accounts on 200 Windows machines would be super painful and plain madness. So you should also spend some time and think about how you are going to reproduce that functionality with your future Linux clients: Will you use e.g. **Ansible** and roll out centrally defined user accounts to every client machine (e.g. semi-centralized approach), or are you going to use **LDAP**? Or are you going to keep **Active Directory** and let Linux users authenticate against it? 

What about **scanners or printers**? What about **mail and calendar**? What about **Office** programs? Did you already conduct tests e.g. with **LibreOffice** and you are 100% sure it will work as a replacement for **Microsoft Office** in your case?  What about **centralised management**?  How are you planning to keep those 200 client machines patched and updated? Have you already experimented with **Salt, Chef, Puppet or Ansible**??


> **jmcguigan2 said:**
>  Is there way to push OS to computers or installation need to be done on each computer?

In theory yes. But you don't want to do that. You don't want to migrate all 200 x machines in one go and at the same time. If anything goes wrong (and *something* will [COLOR="#B22222"]**always**[/COLOR] go wrong!!) then you have sabotaged 200 client machines and 200 x users are prevented from working. I'd rather not want to be in such a situation.

I'd start with "pilot users", e.g. a small group with 5 - 10 clients / users. Migrate them first. Check if it works. Gather feedback from those users: What is working? What is not working? Where do they need improvements? Are features missing? Is functionality missing? Once this "Pilot Phase" is over (after 1-2 months maybe?) and all issues are dealt with I'd go on and migrate the next small group of users.

Again, it is my impression you do not comprehend the complexity of what you are asking. If this is for a business I'd suggest you talk to some IT consulting firms in your area and have them assess the situation. You should probably put this project out to tender and ask for offers. Pro tip: don't go for the cheapest one. Also check their backgrounds and make sure they are qualified (e.g. Xing, Linkedin, Vkontakte, customer feedbacks on their web site...) and don't just try to make a quick buck.

Because if this goes wrong you'll be the one left with 200 x non-working PC's and 200 x angry users + 1 x super angry boss.

---

### Post by TheFu on 2021-06-02
If this is for a university and the plan is to wipe all the computers for Linux over the summer, you can use a number of tools to do that.  The exact distro used AND the exact version of that distro will dictate the answers.  For a long time, Cobbler would be the tool used with a PXE-boot setup.  In 20.04, Canonical changed the installer and how the ISO was laid out, which I hear has broken the prior methods.

If the computers are nearly identical, you could look at using a flash drive and something like Clonezilla to pull the images off the network after booting. Boot into a network-clonezilla setup, start the restore over the network and move onto the next system. Repeat.

In a business, migration of the OS is a huge thing. Failure means people don't work. That means money doesn't come in. As scorp123 wrote, you'll some planning for applications to be used and some pilot users. Start with 1, see how that goes for a few weeks. If successful, add a few more.  The most successful migrations like this will need both end-user support and the entire upper management team support. In most businesses, there will still be a few programs that need to be on Windows and only work on Windows, so ensuring those are retained and accessible as needed needs to be part of the plan.

Don't believe the claims that WINE works flawlessly.  I've found that about 20% of programs work under WINE. That leaves 80% that do not work.  Best to uncover that sooner than later.

If the goal is just to have slightly smart terminals, then Ubuntu wouldn't be the solution I chose.  I'd work on something like a custom **TinyCore** Linux setup.  An entire OS when just the applications needed in 100MB of space.  Applications could be placed on network storage.  TinyCore runs from RAM, so there won't be any faster Linux.  It just comes down to what is needed.  A fast NFS server will make /usr/ mounted over NFS more than fast enough for 200 clients to use.  Heck, people could be given a flash drive with the OS for their group and boot that each day while you are trying to figure this out. Then the Windows OS would still sit on the HDD, ready for use if a fallback is needed.  Consider that cheap 4G USB flash drives are available in bulk, lots of possibilities exist with this method.  4G when 100MB is needed. That leaves a bunch of space, at least while the trials happen.

Start by transferring core infrastructure over, not desktops.  This has been how many companies begin their Linux journey. Do that in a way that end-users don't have to deal with in their face.  Integrating a Linux desktop into a Linux server infrastructure is much easier than trying to connect Linux desktops into {name of proprietary software vendor}.
Most companies begin by replacing file servers and print servers with Linux. This started in the 1990s and is a well-worn solution.

---

### Post by Tadaen_Sylvermane on 2021-06-02
I'm curious what is the primary use of these machines. You may be able to look at a network booted solution altogether. I used LTSP at home. The main developers are people in the Greek school system. It's all but foolproof. Single image to manage. Clients update on a reboot.

[https://ltsp.org/](https://ltsp.org/)

---

