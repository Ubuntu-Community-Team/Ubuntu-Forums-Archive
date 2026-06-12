---
title: "Ok tell me what's so special"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by Derick N Idaho on 2007-12-21
Hi all. I'm a microsoft computer tech and I was curious what all you guys gotta say about this. Just started my download so I gotta few minutes.... what's all your thoughts on this OS?

---

### Post by PmDematagoda on 2007-12-21
If I may ask a question, why does a Microsoft computer tech want to use something like Linux?

---

### Post by Derick N Idaho on 2007-12-21
Ha Ha. Cause I'm just sitting at home bored and was goona check it out. Is it worth my time? Why do you use it?

---

### Post by Craigus on 2007-12-21
[http://www.theopensourcerer.com/2007/11/13/why-use-linux/]("http://www.theopensourcerer.com/2007/11/13/why-use-linux/")

---

### Post by PmDematagoda on 2007-12-21
Yes it is worth your time. But keep this in mind, while Ubuntu is easy to use and get used to, it still is not Windows, so you will have to spend time getting used to the OS and learning about it's different ways of installing and doing things.

Well, for your question, here they are:-

1) It is Open-Source and free.

2) It has virtually no viruses.

3) It is rather simple and fun to use.

4) It is more reliable than Windows XP.

5) It uses much less resources than Windows Vista.

6) It is more customisable than Windows XP.

7) It is more beautiful than Windows XP.

---

### Post by Derick N Idaho on 2007-12-21
Ok I did I read all that. So I'm goona give it a shot. UMM. can I integrate some virus protection before I install? What virus protection do you use?

---

### Post by chewearn on 2007-12-21
Here are two good links by aysiu to read up:
[http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by PmDematagoda on 2007-12-21
> **Derick N Idaho said:**
> Ok I did I read all that. So I'm goona give it a shot. UMM. can I integrate some virus protection before I install? What virus protection do you use?

Hmm, that is really difficult, oh wait, I don't use a virus guard at all:), the thing is that a virus guard is not really necessary with Linux since there are virtually no viruses for it, and the viruses that are there are very inefficient and have never propagated.

But if you still want to use a virus guard then ClamAV, Kaspersky, AVG and Avast! are good choices.

But one thing is that Linux can be hacked by root kits and hackers of sorts if you are not careful. A good firewall I would suggest is Firestarter which can be installed by typing:-

```
sudo apt-get install firestarter
```

You will be asked for the password when you execute this command, one thing is that you will not see the password being typed but do not mind that and just type it as normal.

---

### Post by mali2297 on 2007-12-21
> **Derick N Idaho said:**
> Ok I did I read all that. So I'm goona give it a shot. UMM. can I integrate some virus protection before I install? What virus protection do you use?

You can use AVG, Avast, ClamAV etc after install, but since..
[QUOTE=PmDematagoda]2) It has virtually no viruses.[/QUOTE]
..most of us don't use virus protection.

---

### Post by Sef on 2007-12-21
> But one thing is that Linux can be hacked by root kits and hackers of sorts if you are not careful. A good firewall I would suggest is Firestarter....

That is not quite correct.  Ubuntu comes with a firewall called IPTables.  Firestarter is simply a front-end GUI for it.

---

### Post by PmDematagoda on 2007-12-21
> That is not quite correct. Ubuntu comes with a firewall called IPTables. Firestarter is simply a front-end GUI for it.

Oh yeah, I forgot that, thank you for the correction Sef:).

---

### Post by roaldz on 2007-12-21
> **Derick N Idaho said:**
> Ok I did I read all that. So I'm goona give it a shot. UMM. can I integrate some virus protection before I install? What virus protection do you use?
 
Installing virus protection only for _[these]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses") _viruses is completely unnecessary, it will only consume resources. I know it´s hard to believe, but actually Microsoft is the one that allowed viruses to get as big as they are these days.. Welcome to the Ubuntu Community Derick!

Roald

---

### Post by SteveHillier on 2007-12-21
> **Derick N Idaho said:**
> Hi all. I'm a microsoft computer tech and I was curious what all you guys gotta say about this. Just started my download so I gotta few minutes.... what's all your thoughts on this OS?

I wanted to join this thread but could not think of anything to say that has not already been said in response except.....

It would probably do the world some good if
a)  Microsoft started to accept the Linux existed and made their interface more accessible and 
b)  Microsoft leaned that you can have a viable OS that is stable; that is not big and cumbersome; that works quickly and that does not need a reboot simply because I added a new piece of software or changed a configuration file.

---

### Post by Derick N Idaho on 2007-12-21
Ok OK. i"m catching on. Ummm, ok. thanks guys.  Any other links I can read. "if it ever downloads?

---

### Post by SteveHillier on 2007-12-21
> **PmDematagoda said:**
> 

1) It is Open-Source and free.



I like this part of the response but would just caution.  It is free and most of us involved are techy of some sort and therefore support the product ourselves or via this community.  Support on third party installations it is more difficult because there is less expertise out there

---

### Post by Derick N Idaho on 2007-12-21
Yeah I understand and I appreciate everything.   I'll read to find this but I am running on C: and Can format D: wich is a 70 gig, Can I install Ubuntu on D: and Not worry about it screwing up my C: Windows install?

---

### Post by SteveHillier on 2007-12-21
> **Derick N Idaho said:**
> Yeah I understand and I appreciate everything.   I'll read to find this but I am running on C: and Can format D: wich is a 70 gig, Can I install Ubuntu on D: and Not worry about it screwing up my C: Windows install?

Yes

---

### Post by roaldz on 2007-12-21
> **Derick N Idaho said:**
> Yeah I understand and I appreciate everything.   I'll read to find this but I am running on C: and Can format D: wich is a 70 gig, Can I install Ubuntu on D: and Not worry about it screwing up my C: Windows install?

Yes you can install it on your second hard disk partition as we like to call it. You´ll find the partition manager if you´re going to install Ubuntu. Linux doesn´t use names like ¨C:¨ and ¨D:¨. You´ll get used to that very soon. Please keep in mind that if your going to install it, it will be formatted as ext3, not as fat32 or NTFS. This format is by default not readable by windows. You can install a driver for that though, but that´s another story.
Just burn the livecd and boot it. You´ll like it! Glad to help you.

Roald

---

### Post by Derick N Idaho on 2007-12-21
Ok I'm goona do some more reading. thanks.

---

### Post by roaldz on 2007-12-21
> **Derick N Idaho said:**
> Ok I'm goona do some more reading. thanks.

Please read Ubuntu´s own docs, like wiki´s.

---

### Post by dgoosens on 2007-12-21
hi,

well, might I suggest you check out this:
[http://ubuntuforums.org/showthread.php?p=3968814&posted=1#post3968814]("http://ubuntuforums.org/showthread.php?p=3968814&posted=1#post3968814")

it more or less says it all...

---

### Post by RemmyLee on 2007-12-21
To clarify why viruses are pretty much non-existent in Linux:
Linux handles things in a very unique way. Everything has it's own user space that prevents something like a virus from populating itself. For instance, if a current user were to become infected by a virus, it would not touch another user and would not harm system critical files. It's the way Linux was built. This is of course assuming that you aren't doing something nasty such as using root.

As a Windows tech, you're familiar with Vista's UAC. Well, the premise behind it has been implemented in Linux forever. It's secure by default, and its level of security can be increased.
Another key feature of Linux is the readily available software. There is no need to find an app on the internet. 95% of everything you could ever want is already in the repositories.

Now all this said, Linux isn't for everybody, but as someone with a technical background, I believe you will find it fascinating to say the least. Don't let the simplicity of Ubuntu fool you. At it's core, it is Linux and can be completely customized to your liking. Anything and everything can be changed all the way down to the very system functions.

For me, that's what it's all about. It's not the free software, it's the freedom it gives me. How cool is it to know that you can change, recompile, and then release your own version of almost anything in Linux?

---

### Post by rBGH on 2007-12-21
I very much like that I can install it where ever I want as many times as I want and not be stealing. 

It doesn't come with a ton of crap bundled into it that I'll never use. I can install programs as needed, which are also free.

I can come to the community and ask (politely) about anything to do with the system and am assured to get help when available. I can almost always find help with Google as well. The number one reason why I ditched mainstream support for my computer was the F ed up support I got when I had a problem. My Window ME Compaq Presario was junk from the day I brought it home so I learned something about customer service. (I don't feel that way about all techs since I have gotten great help through my work support network.) 

I have no idea how much it costs to create an operating system but I've come to understand something about corporate America. Simply making profit is not good enough. Products and services are priced according to what the market will bare, and unfortunately many of my fellow consumers don't understand that they have a choice. Also I see no reason to pad some executives over inflated yearly bonus. 

I like the discovery. Something is always happening and I find it very exciting.

---

### Post by DustyRider on 2007-12-21
Some have said it already and we can find many great responses/reasons.

Linux has returned "choice" to the customer, which IMO created customer satisfaction vice, having it shoved down your throat.

Besides it rocks!!!

---

### Post by Sef on 2007-12-21
> I am running on C: and Can format D: wich is a 70 gig, Can I install Ubuntu on D: and Not worry about it screwing up my C: Windows install?

Read [Psychocat's tutorials]("http://www.psychocats.net/ubuntu/index.php").

---

