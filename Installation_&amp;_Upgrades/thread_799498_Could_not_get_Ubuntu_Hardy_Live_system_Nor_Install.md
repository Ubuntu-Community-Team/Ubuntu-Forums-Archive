---
title: "Could not get Ubuntu Hardy Live system Nor Install"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by pbhat on 2008-05-19
My Laptop is Acer Travelmate 2400.I had problems with upgrade to Ubuntu Hardy,so wanted to try fresh install.

I checked the CD for defects,it was passed.When I try the Ubntu Live system,it only brings up a login screen ( sometimes only )and I do not know the username/password for the Live system(Ubuntu/linux ?)But often,it fails to get there too.I have invariably this I/O error (squashfs error) if I go to install from the cdrom boot screen.

I can still run Linux Mint Live based on Ubuntu 7.10 on the same system,but cannot get Ubuntu 8.04 to run live or install.I can get Fedora 9 live to run on the system,but it throws up error if I try to install.It is also prone to lockups while running.

I ran a memory test.No errors there.I have 1.5GB RAM.So less RAM is not the problem.Upgraded U(K)buntu / Opensuse 10.3 also run on this system.I cleaned my DVD Rom drive head.I ran a full length movie to rule out any error in the Drive.

I cannot make out if this is a machine problem or OS problem.The tests I did all should have shown up any machine problem,if existed.But wondering if these OSes have overtaken this machine with 1.5 GHz processor,1.5 GB RAM!

Thanks in advance to anybody who suggests an answer.

---

### Post by iaculallad on 2008-05-19
The problem is you are using a remastered Ubuntu Hardy. That's the reason that its asking you a username and a password. For a fresh start, I won't recommend you using that medium. Try downloading a fresh ISO copy of Hardy Heron (test its MD5 hash and burn it at a lower speed, say 4x). Use that to install your Hardy.

*Just for test: If you created that CD, try using root as username and the password for the root.

---

### Post by pbhat on 2008-05-19
Dear iaculallad,

Thanks for the reply.
Remastered?I burnt from an iso.But my co-worker burnt the iso I downloaded.May be something has gone wrong there,however unlikely I thought that.

---

### Post by iaculallad on 2008-05-19
> **pbhat said:**
> Dear iaculallad,

Thanks for the reply.
Remastered?I burnt from an iso.But my co-worker burnt the iso I downloaded.May be something has gone wrong there,however unlikely I thought that.

Yap, Remastered? The process of where you could customize a LiveCD/DVD of Ubuntu and its Derivatives. Take a look at this [link]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") for some ideas on how they do it.
Usually, if you did the Remaster on Ubuntu "already installed" on your HDD, it copies permissions/passwords/users that are currently used, so prompting you password upon installation. But still, there are workarounds on doing it the right way without copying existing permissions/passwords.

---

### Post by pbhat on 2008-05-20
Hi,
I reburnt the iso myself and tested on my notebook.Ubuntu Live often fails,when it runs,it only brings up login screen.If I switch to Console,I can see error message 'underlying user not known to authentication module' Error message.Also,the console is full of messages on broadcaom wireless firmaware absence.

But the CD(iso) itself is good,as it runs perfect on other system-(Other PC)I am wondering what could be bothering it,as CD test,Memory Test,does not throw up any error,on the notebook.

---

### Post by iaculallad on 2008-05-20
This seems like an existing installation error and not a LiveCD error.
What if you do this:
Get yourself other [bootable partitioning software]("http://gpartedclonz.tuxfamily.org/") (not the Ubuntu LiveCD) and try deleting your Laptops current partitions (knowing that you only did a fresh install so I guess no important data was saved). Afterward, restart your laptop, insert your Ubuntu LiveCD and let it do its job.

---

### Post by pbhat on 2008-05-20
It beats me why Ubuntu in Live mode should be bothered by the existing installed Ubuntu version.I understand the alternate CD is designed to upgrade offline,it should be bothered by the existing installation.

Surprisingly,I tried once again the same CD,everything went fine,Ubuntu Hardy got installed.But sadly,it gives me no option to enable my broadcom wireless for network.It doesnot even tell me I need firmware though I know it from my previous experience.As if Ubuntu has taken a step backward!

Thank you for your kind involvement.

---

