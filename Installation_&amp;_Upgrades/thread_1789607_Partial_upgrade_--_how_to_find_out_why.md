---
title: "Partial upgrade -- how to find out why?"
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2011-06-24
(This is a request for information, not for a fix.)

I use Lucid 64-bit.

This morning, I ran Update Manager, and it gave the following error:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=195848&stc=1&d=1308897846[/IMG]

How can I find out the reason behind this? (It concerns Firefox, which I upgraded to version 4 because of persistent errors in version 3. I have the PPA [FONT=Courier New]http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu lucid main[/FONT].)

The command line gives the following results:
```
$ [COLOR=Blue]sudo apt-get upgrade[/COLOR]
The following packages have been kept back:
  firefox
The following packages will be upgraded:
  firefox-branding firefox-gnome-support language-pack-en language-pack-en-base
```Synaptic Package Manager does something different. It will allow me to update, but on condition that it removes package [FONT=Courier New]firefox-globalmenu[/FONT].

Clearly, there is a clash with the [FONT=Courier New]firefox-globalmenu[/FONT]; but how do I find more information?

---

### Post by zoubidoo on 2011-06-24
I got this too on my 10.04 system.  Someone somewhere made a cockup. 

Looking at my command line history I fixed it with:

```
sudo dpkg -r xul-ext-ubufox ubufox
sudo apt-get -f upgrade 
```

But firefox is still being held back.

---

### Post by Paddy Landau on 2011-06-24
> **zoubidoo said:**
> ```
sudo dpkg -r xul-ext-ubufox ubufox
```But firefox is still being held back.
I don't have ubufox installed on my machine. According to my Synaptic, it's not ubufox but firefox-globalmenu that needs removing. I don't know what firefox-globalmenu does, but it seems to be for Unity, which I don't use. You may want to try that.

I'll wait for a day or so to find out if it someone manages to fix it.

But I'd still like to know how to get the relevant information -- why is it being held back?

---

### Post by plucky on 2011-06-24
I had the same this morning.

If you run the check again in update manager it will find two new security upgrades and also install the Firefox upgrade.

Or you can run ```
sudo apt-get update && sudo apt-get dist-upgrade
```


Good Luck

---

### Post by rawlins02 on 2011-06-24
Same here. I'm not allowing the suggested partial upgrade, since I don't know what an upgrade will do. I want to do a normal update, not upgrade the 10.04 distribution, I presume.

---

### Post by Frogs Hair on 2011-06-24
I had a partial upgrade once and it was due to a package not being available . After reading a couple horror stories I decided to wait and soon the package was available and all packages installed normally . This happened with a 10.04 distribution upgrade and I have never seen a partial upgrade since.

---

### Post by Paddy Landau on 2011-06-24
> **plucky said:**
> ```
sudo apt-get dist-upgrade
```> **Frogs Hair said:**
> This happened with a 10.04 distribution upgrade and I have never seen a partial upgrade since.
Well, I stick to the LTS releases, and so I will not do dist-upgrade. I have this error on the normal updates.

I will do as Frogs Hair suggested and wait a couple of days to find out whether it is solved; if not, I'll uninstall firefox-globalmenu (it seems to be for Unity, not Lucid) and run the update.

My original question is still not answered, though... How do I find out why firefox is being held back? What command do I run?

---

### Post by plucky on 2011-06-24
> Well, I stick to the LTS releases, and so I will not do dist-upgrade. I have this error on the normal updates.

All a dist-upgrade will do is try to resolve dependency problems which caused the "partial upgrade" problem.The normal upgrade will not resolve dependency problems.
I too am running 10.04.2 LTS on two machines and the dist-upgrade fixed the problem and I am still on 10.04.2 LTS.

Good Luck

---

### Post by Paddy Landau on 2011-06-24
Well, that perplexed me -- I thought dist-upgrade took you to the next release!

I just did a dist-upgrade with the --dry-run option (to see what it would do), and you're right; it would uninstall firefox-globalmenu before upgrading Firefox.

I learn something new every day, thank you!

Still, I will wait for a couple of days as per my first decision.

I think this has also answered my question: To find out why there's a partial upgrade, run
```
sudo apt-get --dry-run dist-upgrade
```I shall mark the thread as solved.

---

### Post by libssd on 2011-06-24
Tribute to Ubuntu. This is the first update error I can recall in 3 years of using Ubuntu, and I quickly found the answer here; time to solution: < 1 minute.

In comparison, I spent half a day setting up a brand new Win7 computer for a friend this week, and the process was filled with multiple error messages.

---

### Post by Paddy Landau on 2011-06-25
> **libssd said:**
> Tribute to Ubuntu. This is the first update error I can recall in 3 years of using Ubuntu...
It's not even an error, is it? It's a warning, and it prevents you from installing something that clashes. Although it's not the first time I've had this (past experience indicates that time will solve the problem), I agree with you -- Ubuntu has given me fewer problems in a year than Windows used to give me in a month.

---

