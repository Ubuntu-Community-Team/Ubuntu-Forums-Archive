---
title: "HELP installing MEEP!!!!!!!!!!!!!!"
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by MrsChips on 2013-01-22
I really need help desperately

I need to install MEEP but to do so I need Ubuntu which I've managed to install; I've never used Ubuntu in my life and don't have clue how to install MEEP. I downloaded the MEEP file and apparently you can install it from the terminal using just one line which I tried to do but it just comes up with error;

could not open lock file /var/lib/dpkg/lock-open (13:Permission denied)
unable to lock the administration directory (/var/lib/dpkg/) are you root?

WTF does that mean????? how don't i have goddamn permission to stuff on my own computer and I'm administrator??? do I need to move MEEP file to some other stupid folder???

Help!!!

Ubuntu i'm using is 12.04 LTS

---

### Post by dgharmon on 2013-01-22
> **MrsChips said:**
> I need to install MEEP but 

What's MEEP, do you have a link for MEEP?

---

### Post by MrsChips on 2013-01-22
yeah its this version here: [http://ab-initio.mit.edu/wiki/index.php/Meep_Download](http://ab-initio.mit.edu/wiki/index.php/Meep_Download)

MEEP is basically an electromagnetic simulation software package, it needs lots of prerequisites but apparently this download includes all of them...i think

Thanks so much for even reading this!!!

---

### Post by darkod on 2013-01-22
Without looking into details how MEEP installs, if it asks you about root permissions you need to put 'sudo' in front of the command you tried.

Ubuntu tries to protect you from unintended damage and most system commands need to be run with sudo in front.

Let us know how it goes.

PS. When you use sudo, it will ask you to retype your own password again, for added protection. Just retype it and hit Enter, it's your own password.

---

### Post by Cheesemill on 2013-01-22
You just need to prefix the command with sudo....
```
sudo apt-get install meep h5utils
```

---

### Post by MrsChips on 2013-01-22
Holy mother of god it did something...

OK in the terminal the last line says
ldconfig deferred processing now taking place 

and now its just waiting for newline so i'm guessing its done it?  I ran the 'meep' command and now getting
 
meep> 

so I guess that now means i need to read tutorial!

I will probably pester later when problems crop up because I'm nervous I haven't installed all the needed prerequisites but otherwise thank you so much!!! you are amazing!!!

---

### Post by Cheesemill on 2013-01-22
> **MrsChips said:**
> I will probably pester later when problems crop up because I'm nervous I haven't installed all the needed prerequisites but otherwise thank you so much!!! you are amazing!!!
You have installed everything. By using the apt-get command all dependancy resolution is automatically carried out for you. If you look back at the output of the command you ran I'm guessing that it will have installed a lot more than just the meep and h5utils packages. These are all of the prerequisites that you needed.

I'd also like to point out that you didn't have to download the meep file yourself (it wasn't needed or used). This is all taken care of for you when you use apt-get.

---

### Post by MrsChips on 2013-01-22
Ahh ok, thank you so much for explaining this to me, will definitely be doing some tutorials on Ubuntu as well

---

### Post by Blackkitten on 2013-01-22
> **MrsChips said:**
> Holy mother of god it did something...

...

I can't be quite. This makes me smile ;)!
Glad you resolved your problem.

---

