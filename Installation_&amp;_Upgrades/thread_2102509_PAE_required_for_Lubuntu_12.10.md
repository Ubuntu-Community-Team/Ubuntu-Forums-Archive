---
title: "PAE required for Lubuntu 12.10?"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by VanillaMozilla on 2013-01-07
The installation disk is said to require PAE, but I assume I can update safely without a PAE-enabled processor?  Has anyone done this for sure?

EDIT:  It turns out, after this thread was done, my processor has PAE and I didn't realize it.  Some very old processors have pae.
~$ cat /proc/cpuinfo | grep pae
flags		: fpu vme de pse tsc msr **pae** mce cx8 apic mtrr pge mca cmov pse36 mmx fxsr sse up

EDIT AGAIN:  It does, however, lack NX-bit capability and has little memory installed, so there's absolutely no reason to use the PAE kernel.  It runs with either the pae or non-pae kernel, although theoretically, the non-pae kernel may be faster.

---

### Post by forkandles on 2013-01-07
This should fix it:
[http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html](http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html)

---

### Post by ajgreeny on 2013-01-07
You can update from 12.04 to 12.10, if that's what you mean, as 12.04 did not use a pae kernel by default in Lubuntu 12.04.

I do not know how it will be possible in future, once updating from 12.04 is no longer an available option; presumably another distro entirely will be needed, or perhaps someone will fork a version of the .iso that has a non-pae kernel.

@ forkandles.
Thanks for that info.  Not needed personally but useful to be aware of!

---

### Post by VanillaMozilla on 2013-01-07
So it's a kernel problem.  With that information I found some more links.
[https://lists.ubuntu.com/archives/ubuntu-devel/2012-May/035180.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-May/035180.html)
[http://askubuntu.com/questions/182048/will-it-be-possible-to-use-a-non-pae-kernel-in-12-10?rq=1](http://askubuntu.com/questions/182048/will-it-be-possible-to-use-a-non-pae-kernel-in-12-10?rq=1)
[http://bazaar.launchpad.net/~webtom/+junk/linux-image-i386-non-pae/files](http://bazaar.launchpad.net/~webtom/+junk/linux-image-i386-non-pae/files)

Unfortunately, I have had no luck in creating a bootable USB drive.  Looks like it might be simplest to make that computer a legacy computer.  Thanks.

---

### Post by VanillaMozilla on 2013-01-07
OK, I've got a test machine.  I'll just try it.

---

### Post by forkandles on 2013-01-07
VanillaMozilla,

Initially I had problems creating a bootable USB drive.

I had no joy with StartUp Disk Creator, so I used Unetbootin (second answer down): 

[http://askubuntu.com/questions/154299/why-isnt-startup-disk-creator-working-in-12-04](http://askubuntu.com/questions/154299/why-isnt-startup-disk-creator-working-in-12-04)

Before this, I formatted the USB drive:
[http://freshtutorial.com/format-pen-drive-usb-external-drives-linux/](http://freshtutorial.com/format-pen-drive-usb-external-drives-linux/)

The USB stick must also be mounted. 
In my case:

```
sudo mkdir /media/Corsair

sudo mount /dev/sdc1 /media/Corsair
```

In the BIOS set USB drive to boot first and you should be okay.

---

### Post by VanillaMozilla on 2013-01-07
Thanks, I'll try that for making a bootable USB disk.

Test machine is updating, and looks normal so far.  I can check it in a few hours.

---

### Post by VanillaMozilla on 2013-01-08
Well I'll be darned.  I now have a 3.2.0-35-generic kernel with Gnome 3.6.0.  (Almost) normal update.

---

### Post by amjjawad on 2013-01-23
> **forkandles said:**
> This should fix it:
[http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html](http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html)

+1

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

I'm discussing right now with another team member of my team (Lubuntu) whether to add that link or not. We had a discussion last week on here: [https://www.facebook.com/groups/lubuntu.official/](https://www.facebook.com/groups/lubuntu.official/)

and I think that will help other users who are not aware of that link. Fact is, not everyone reads the Wiki Pages. Sad but true!

Edit:
It is mentioned here by the way: [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/Lubuntu#System_Requirements](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/Lubuntu#System_Requirements)
That starting from 12.10, it requires PAE-CPU - just for the record.

---

### Post by VanillaMozilla on 2013-01-23
Thanks very much for your interest in this.

> **amjjawad said:**
> +1
It is mentioned here by the way: [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/Lubuntu#System_Requirements](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/Lubuntu#System_Requirements)
That starting from 12.10, it requires PAE-CPU - just for the record.
Actually, it says the non-PAE ISO is not available, but it doesn't say that I *can* actually *update* a non-PAE system.  That was the question.  This is important for people who will think that this is the end of the line for Ubuntu and Lubuntu on many older computers, when in fact they could update.  I would suggest a note about this in the System Requirements and in this link -- and wherever it says that PAE is required.

> **amjjawad said:**
> +1
I'm discussing right now with another team member of my team (Lubuntu) whether to add that link or not. We had a discussion last week on here: [https://www.facebook.com/groups/lubuntu.official/](https://www.facebook.com/groups/lubuntu.official/)

and I think that will help other users who are not aware of that link. Fact is, not everyone reads the Wiki Pages. Sad but true!

I don't have a facebook account, so I can't read the discussion, but the article looks good to me, and a link never hurts.  The fact is that the Wiki pages do a very good job of giving a well-written basic overview.  If I could offer a suggestion, it would be for much more of the same. 

It would be extraordinarily useful if the Wiki pages could be expanded to tell how these systems are put together.  It's often quite difficult to get needed information on configuration in a concise, consistent, and comprehensible form.  For example, it would state what window manager is used, how to start the configuration GUI and command-line UI (including the names of the programs so they can always be started!), the names and locations of the configuration files, and preferably what the various options mean, etc.  It would give basic information such as a list of system programs distributed with the desktop, and their corresponding config info, etc.  It would tell how to edit a menu, how to start and stop basic system services, how to configure a search tool (so it actually finds your files!), and much more.

The information would not have to be lengthy; much of it could even be in table form.  It would *not* give a keystroke-by-keystroke narrative of how to do certain operations (that would not be concise!).  Clarity, brevity, structure and (hopefully) completeness would be the objectives.  I can't stress enough how much of a help it would be to have proper documentation -- or even, just . . . documentation!  I know a lot of information is available, but much of it is fragmented, scattered, outdated, and opaque.  Ubuntu used to have a built-in system Help document that had some of this information, but it seems to be temporarily MIA.

---

### Post by VanillaMozilla on 2013-01-24
A brief comment about documentation, and I hope you read this.  One way to get people to read the Wiki page is to make it easy to find.  I think you need to pay more attention to links at the highest levels.  Here's an example.

I see that many of the topics I mentioned in my previous post are covered *in part.*  But when I had a tough problem with LightDM, here's how I had to find information (albeit much too late to help).  I checked Google for Lightdm, and found this:
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM) .
That's nice, but how would I find it?  It's difficult or impossible to get there from the front page.  Here's the front page:
[https://wiki.ubuntu.com](https://wiki.ubuntu.com) .
Can you find the information from there?

It's easier if you start from help.ubuntu.com.  Again, all this needs to be much easier to find.  (Incidentally, I have some of this information at one time or another, but in this case I found it long after I had solved a problem the hard way, with a lot of perseverence and luck.)

---

### Post by amjjawad on 2013-01-24
VanillaMozilla,

On behalf of Lubuntu Team, allow me to thank you for sharing such valuable suggestions and notes. We are keen to listen to our users, take notes and work so hard to achieve the best result.

You may or may not know that Lubuntu Team is small in numbers but huge in quality and achievement and I'm not saying we are prefect but we are the best in what we do and I'm talking about the whole team, the one family of Lubuntu that I'm honored to be a member of.

Now, let's talk business.

I shared exactly the same thought of yours before. Why not to have for example a link of Lubuntu Wiki on the main Wiki pages of Ubuntu? then, after getting my hand dirty and dive deep in the details, I came to know that it is not really necessary for that as things work little bit different than what I thought.

When someone has a problem, regardless of what is the problem is/could be, he/she simply use Google.
How it works?
If you just type "lubuntu", you will on the first page of the result all the main links of Lubuntu that one may needs.

Trust me, you need to bookmark these:

[B][https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)
[https://help.ubuntu.com/community/Lubuntu](https://help.ubuntu.com/community/Lubuntu)
[https://wiki.ubuntu.com/Lubuntu/ContactUs](https://wiki.ubuntu.com/Lubuntu/ContactUs)
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755) OR [https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)
[/B]

On these links, I'm sure you can start your journey. I know you may disagree with me at this point but I really hope you see it from a different point of view.
This is how it works.

Also, it is very helpful to use: [www.googlubutu.com](www.googlubutu.com)

Now, if you still disagree with me, that is fine with me and actually it is healthy and for this, I strongly recommend to join us and start a discussion on one of our official channels - you can find that on the Contact Us page.

This is how to join: [https://wiki.ubuntu.com/Lubuntu/GettingInvolved](https://wiki.ubuntu.com/Lubuntu/GettingInvolved)

One of my task on Lubuntu Family is to take care of the Wiki Pages but to be honest, the people who work on that area are very few.
That is why, we are always looking for more people who can add a value.

I used to be a very good HOWTO Writers until something happened that changed that. Now, I'm more into the Communications and Support Tasks.

So, you and everyone else are very welcome to join and share your ideas and help this promising community to grow bigger and better.

We seek quality not quantity :)

I was just a user of Lubuntu and when I wanted to understand what is going on behind the scenes, I simply joined the team to understand better and tell you the truth, there are tons of stuff that I don't really understand (specially the programming part - I'm not a developer and not even close to be) but in the same time, that is the fun part as you always feel hungry for knowledge and to know more and more.

Thank you so much once more and sorry if I wrote too much. I get excited easily :P

---

### Post by amjjawad on 2013-01-24
I have added the link to:

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/Lubuntu#System_Requirements](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/Lubuntu#System_Requirements)

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Introduction](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Introduction)

:)

---

### Post by VanillaMozilla on 2013-01-26
Wow, thanks for your enthusiastic reply.  I definitely have bookmarked those links.

I do believe strongly, though that if a Web site is intended to be read, then everything should be easily accessible by following a few links from the front page.  The Ubuntu Wiki fails that test badly, although parts of it are otherwise quite excellent.  You have done a great job on that documentation.

I have found parts of the Wiki through Google, but I'm not sure Google is a good substitute for structure, since it doesn't provide the structure, and mixes the results with many other links.

I might contribute to the Wiki at some time, but first I have some bugs to report and things to figure out.  Thanks again for your help.

---

### Post by amjjawad on 2013-01-26
I'm at your service anytime and you are most welcome, I have done nothing much but thanks a lot for your nice words :)

I always take the path which has this sign: "Be the change you want to see around you" and yes, it is not an easy path but it's so wonderful and nice full of challenges.

You are welcome to join anytime whenever you feel ready :)

---

### Post by VanillaMozilla on 2013-05-01
I thought I had checked and found that my processor lacks PAE, but it turns out, that's not true.  That makes the documentation on this somewhat of a moot point, I believe.

It turns out that many more processors have PAE than I realized.  I am informed that Pentium II and Pentium III processors have PAE.  I didn't check that, but at least my own has it.  Here's the diagnosis.

~$ cat /proc/cpuinfo
model name	: Pentium III (Coppermine)
...
flags		: fpu vme de pse tsc msr **pae** mce cx8 apic mtrr pge mca cmov pse36 mmx fxsr sse up


EDIT:  It turns out, though, that my Pentium III lacks NX bit capability.  PAE does two things:  It extends the address space to use more than 4 GB of memory, and it enables the NX bit.  It also uses a more complex method of addressing instructions, which may make the computer run a little slower.  However, since the computer has <1 GB of memory and lacks NX capability, there is no reason to use the PAE kernel.  I have tested, and it works either with or without.  The PAE kernel uses a more complex memory-addressing method, so theoretically it may run slower.

If I knew how, I would mark this thread as solved.

---

