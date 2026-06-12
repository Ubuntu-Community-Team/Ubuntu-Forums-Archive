---
title: "missing final newline in deb file"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by Andred on 2006-12-26
Hi Guys
I have just installed 6.06LTS off the CD onto a compaq nx9010.
I had a few issues using using USB stick and power mnagement so decided to activate the package update icon on the top bar.

It took forever with the speed getting slower and slower. 
Eventually after numerious restarts and 2 boots I got all the packages loaded ready to install and in true windoes form

[INDENT][I]The following problems were found on your system: 	

E: /var/cache/apt/archives/dpkg_1.13.11ubuntu7_i386.deb: files list file for package `powermanagement-interface' is missing final newline[/I][/INDENT]

Now, how do I delete this file and how do I get a "new" one.

I have tried to pull a new one from a mirror server but cannot drop it into the archives directory. And try as I may I cannot work out how the Package Manager works.

Regards
Andre

---

### Post by foolsh on 2006-12-26
issue the command 
sudo apt-get clean
to clean out the repository cache

then try
sudo apt-get -f install

tell me if this helps

---

### Post by Andred on 2006-12-27
Not a sausage.
Same Error after a very long down load of all 339 upgrades again.

So Where do i get a new power mangement-interface package?
How Do I download that package only.....?
Or what do i edit to add a New Line at the end?
Do I need to use sudo to get into supervisor mode to do this.
Is it safe to use the ignore on apt-get to do this install from the Terminal.

Help please, been a dos/windos jockey up to this point.

Regards
Andre

---

