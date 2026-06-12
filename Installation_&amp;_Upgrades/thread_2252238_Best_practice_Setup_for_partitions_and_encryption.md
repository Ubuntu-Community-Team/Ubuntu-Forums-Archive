---
title: "Best practice: Setup for partitions and encryption"
date: 2014-11-10
forum: Installation &amp; Upgrades
---

### Post by zegerman on 2014-11-10
Hi,

I am new to ubuntu and I want to find a good setup for my Dell e7440. 

There are 2 questions I am struggling with 
1) what's the best partition setup
2) what's the best / most efficient way to secure my data

I believe these are questions that every user would ask themselves before setting up a system.
Unfortunately I couldn't find a clear answer on the web and therefore ask you for advise.

My goal is simple: 
Find a partitioj setup that allows an easy future change if I want to move to other distros
Efficiently secure my personal data (development code, documents, pictures) in case the my laptop is lost/stolen


1. Separte Home partition vs one System partitions

I wanted to go with one partition just to make most of the disk space.
Many posts advised on going with a separate /home partition since it will make life easier down the road e.g. reinstalling

Therefore I think a separate home partition is the way to go.

What do you agree?


2. Home encryption vs Full Encryption vs Truetrypt

Having a separate home parition what would be the recommended and most efficient encryption setup?

Are there any downsides that I should be aware of when having 
1)a home partition encryption?
2)truecrpyt container


Can I go with full encryption setup if I have a separate home partition?
Is it possible to reinstall the system and being able to access the home paritions afterwards?

Cheers

---

### Post by sudodus on 2014-11-10
> **zegerman said:**
> Hi,

I am new to ubuntu and I want to find a good setup for my Dell e7440. 

There are 2 questions I am struggling with 
1) what's the best partition setup
2) what's the best / most efficient way to secure my data

It depends on what you want to achieve. What level of security, how easy to use and backup ...
> 
I believe these are questions that every user would ask themselves before setting up a system.
Unfortunately I couldn't find a clear answer on the web and therefore ask you for advise.

My goal is simple: 
Find a partitioj setup that allows an easy future change if I want to move to other distros

An encrypted system is more difficult to port to another computer or distro
> 
Efficiently secure my personal data (development code, documents, pictures) in case the my laptop is lost/stolen

1. Separte Home partition vs one System partitions

I wanted to go with one partition just to make most of the disk space.
Many posts advised on going with a separate /home partition since it will make life easier down the road e.g. reinstalling

Encrypted home is easier to manage than encrypted disk. I think separate home partition does not change the security, but there are other advantages.
> 
Therefore I think a separate home partition is the way to go.

What do you agree?


2. Home encryption vs Full Encryption vs Truetrypt

Truecrypt is no longer developed.
> 
Having a separate home parition what would be the recommended and most efficient encryption setup?

Are there any downsides that I should be aware of when having 
1)a home partition encryption?
2)truecrpyt container

I think full encryption will give you a higher lever of security than encrypted home. It is possible to have both at the same time. See this link (it is for testing, but shows how to install such a system).

[http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73663/testcases/1439/results](http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73663/testcases/1439/results)
> 
Can I go with full encryption setup if I have a separate home partition?
Is it possible to reinstall the system and being able to access the home paritions afterwards?

Cheers

Remember that there is no way to recover the system, if you forget the passphrase and the password, when the system is encrypted !!!

It is also extra important to have a good and frequent backup system.

---

### Post by nerdtron on 2014-11-10
> 1. Separte Home partition vs one System partitions

I wanted to go with one partition just to make most of the disk space.
Many posts advised on going with a separate /home partition since it will make life easier down the road e.g. reinstalling

Therefore I think a separate home partition is the way to go.

What do you agree?

I disagree to this. I think it would be better to have just one partition for the whole Linux system. Now where do you put your data? Create a big partition on where you will save your data. Think of it like a D: drive in windows. Just mount that partition as say /data and dump everything there.
Advantage of this is easier migration/reinstallation of any linux OS. You always have a separate data partition without any linux residues from previous installs.

Now if only we can figure out encryption.

---

### Post by zegerman on 2014-11-11
Hi,

Thank you for your feedback.

Just to be clear what I want to achieve:
- Securing personal data (e.g. dev code, database content, documents. picturd, emails etc.) from being viewed after notebook is stolen or lost. 
- Making sure the data can still access after coruption or reinstallation of the system
- Allow easy automized backup.

Maximum effort that I am willing to take is entering up to 3 passwords ONCE on startup.
After that I mostly put my laptop to sleep or hibernate. So there shouldn't be any other passwords besides login password after wake up.


I summarized the option that I am currently seeing with some comment.
Which one do you prefer?


1. no Encryption - one system or separate /home or separate /data
=> no security. no solution.


2. /home encryption with separate /home
=> I dont see the advantage over the fulldisk encryption. I guess it is less limiting???


3. Full encryption
a) separate home
=> not sure if that works out of the box. limiting since I could install another distro alongside.

b) no separate home
=> easiest option but limiting since I could install another distro alongside.

c) no separate home but separate /data
=> not sure if that works out of the box => in that case I would rather go with separate home since I dont see the advantages.


4. Encrpyted Container on separate /data partition
=> The idea of having a separate data folder sounds very good to me. 
I know that truecrypt is developed anymore but version 7.1. is still save to use from what I read.
This might the most flexible solution since I could access that also from a VM with Windows.
But could I move the database files, web root etc to the container easily?

cheers

---

### Post by sudodus on 2014-11-12
> **zegerman said:**
> Hi,

Thank you for your feedback.

Just to be clear what I want to achieve:
- Securing personal data (e.g. dev code, database content, documents. picturd, emails etc.) from being viewed after notebook is stolen or lost. 
- Making sure the data can still access after coruption or reinstallation of the system
- Allow easy automized backup.

Maximum effort that I am willing to take is entering up to 3 passwords ONCE on startup.
After that I mostly put my laptop to sleep or hibernate. So there shouldn't be any other passwords besides login password after wake up.

The computer is much safer when shut down compared to sleeping or hibernating.
> 

I summarized the option that I am currently seeing with some comment.
Which one do you prefer?


1. no Encryption - one system or separate /home or separate /data
=> no security. no solution.


2. /home encryption with separate /home
=> I dont see the advantage over the fulldisk encryption. I guess it is less limiting???


3. Full encryption
a) separate home
=> not sure if that works out of the box. limiting since I could install another distro alongside.

b) no separate home
=> easiest option but limiting since I could install another distro alongside.

c) no separate home but separate /data
=> not sure if that works out of the box => in that case I would rather go with separate home since I dont see the advantages.


4. Encrpyted Container on separate /data partition
=> The idea of having a separate data folder sounds very good to me. 
I know that truecrypt is developed anymore but version 7.1. is still save to use from what I read.
This might the most flexible solution since I could access that also from a VM with Windows.
But could I move the database files, web root etc to the container easily?

cheers

I think full encryption will give you a higher level of security. With and encrypted container on separate data partition, there are risks that temporary data are found in several places, for example the swap partition and the temporary directory (/tmp).

I would not recommend Truecrypt, but use it if you think it is safe. It is much better than no encryption, but might not stop the intelligence service organizations of the superpower countries. Other intruders might use other methods ;-)

---

### Post by zegerman on 2014-11-12
The picture describes it very well.
I am not looking for high security solution since my data is not very critical. Therefore I dont mind to expose tmp or swap.

I just want to have simple protection of my data if the notebook is lost.

What do u think of the options? Are they all doable?

---

### Post by sudodus on 2014-11-12
I think all of them are doable. I made an 'encrypted home' pendrive a couple of years ago. Home was a directory in the root partition. Such a system has cryptswap, which can cause problems if booted in a linux computer. It encrypts the internal swap so that it needs repair in order to work with its original operating system. My conclusion is that an installed system in a pendrive should not be able to create (convert to) cryptswap (I did that). This is not a problem in a normal installed system in a laptop.

I think encrypted home is simpler than a completely encrypted drive, and it works well. You hardly notice that it is there.

---

### Post by zegerman on 2014-11-13
Fyi.. I went with separate encrypted home. It seems to be the best compromise between security and flexibility but I guess the future will show if it works out. Thanks for ur help. 
Cheers

---

### Post by sudodus on 2014-11-13
Good luck, and let us know how it works for you :-)

If and when you are happy with the solution, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by mastablasta on 2014-11-13
good choice, but remember to do regular backups as if you forgot the password or even if crucial part of disk gets corrupted you loose everything (the data).

---

