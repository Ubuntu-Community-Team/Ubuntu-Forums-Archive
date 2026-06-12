---
title: "fresh installatie restore settings"
date: 2015-04-04
forum: Installation &amp; Upgrades
---

### Post by leobos2 on 2015-04-04
Hi guys,

I recently had a triple boot with osx, win and of course Ubuntu. I installed it on 2 ssd's and the Ubuntu on a 10k HDD. Using osx less and less and using Ubuntu more and more I wanted to install Ubuntu on 1 of the ssd. So I did, I have a triple boot of win, ubu15.04, and ubu14.10.

What is the best way for me to get all the settings from the 14.10 to the 15.04? 

I have read many many threads with too many different approaches. What is the easiest way to do this? I would love to do a simple restore if I install on a different PC/laptop.

---

### Post by TheFu on 2015-04-04
Depends on what you mean by "settings" and what you consider "easy."

System settings are normally stored under /etc/.
User settings are normally stored in the HOME of that userid.
If you installed any other programs, those settings may be placed elsewhere if they don't follow the model of /etc/ and $HOME.  For example, extra themes or some commercial programs like /opt/ and some web servers like /var/www and don't forget any databases.

Some of these settings (just a few) are highly specific to the exact installation, so copying everything from 1 install to another is not advised.  For example, the fstab and anything under /etc/udev/. 

So - while you can see the settings aren't usually in odd places, they "may" be in odd places. Only you will know what has been installed outside the normal package manager stuff and if any settings are in non-standard places. If you always stay with package manager software and don't override the default locations, it can be easy.

With all that said, howtogeek had an article about some tool that backs up settings for ubuntu. They had 20 pgs of screen shots to explain it. In this case, the GUI is NOT easier than the shell/CLI method. Actually wrote a blog article [http://blog.jdpfu.com/2015/01/04/linux-gui-tools-easier-not-always](http://blog.jdpfu.com/2015/01/04/linux-gui-tools-easier-not-always) about this.

---

### Post by leobos2 on 2015-04-05
Thanks TheFu,

I saved all the settings like you said, plus a tip I got from another forum. Using aptik. 
So now my system is up and running, and all of the settings are back where they belong. Even the extra buttons on my mouse are working. And I love the speed of the SSD, makes a big difference :-D

---

### Post by Topsiho on 2015-04-05
Hi leobos2,

If you have a separate /home partition, you could try keeping it (to not format it) during the install of the newer version of Ubuntu. I never had problems doing so.
If not, I guess that you'll have to do the settings (instellingen) again while using your applications (programma's).
Why do you use the interim versions of Ubuntu, which are supported for only nine months, and not the LTS-versions, which are supported for 5 years, and are far more stable?

Groeten, ook van Tom Poes en Heer O.B. Bommel,  :)

Topsiho

---

### Post by TheFu on 2015-04-05
> **Topsiho said:**
> 
Why do you use the interim versions of Ubuntu, which are supported for only nine months, and not the LTS-versions, which are supported for 5 years, and are far more stable?

I agree completely.
For me, non-LTS releases don't make any sense and aren't worth my time. However, for some people their hardware is very new and support for it may not exist in 14.04, so running a newer release might be the lessor evil.  As an example, my chromebook touchpad isn't supported by the 14.04 kernel but is by the later released kernels. After every kernel update, I have to manually compile and install the touchpad drivers. For me, it is a minor inconvenience and scripted. For many users, it would be an impossible situation.  I'm just lucky the drivers exist at all.

---

### Post by leobos2 on 2015-04-06
> **Topsiho said:**
> Hi leobos2,

If you have a separate /home partition, you could try keeping it (to not format it) during the install of the newer version of Ubuntu. I never had problems doing so.
If not, I guess that you'll have to do the settings (instellingen) again while using your applications (programma's).
Why do you use the interim versions of Ubuntu, which are supported for only nine months, and not the LTS-versions, which are supported for 5 years, and are far more stable?

Groeten, ook van Tom Poes en Heer O.B. Bommel,  :)

Topsiho

I wanted to use the 14.04 disk as my new /home, and it was both an experiment if I could get all my settings and programs to a new installation. It would be very useful for me to have a good running system as a base for any new installation. That being said, I have noticed a big improvement in speed with the 15.04 installation. But I can't be sure if it's the SSD or the new version. 

en doe ze de groetjes terug ;-)

---

### Post by TheFu on 2015-04-06
It is the SSD. No question.

---

### Post by Topsiho on 2015-04-06
Hello leobos2,

I must say that I don't understand what you are trying to tell us with "I wanted to use the 14.04 disk as my new /home".
A typical install of Ubuntu (or other Linux), with a separate /home partition, is that on the hard disk(s) separate (aparte) partitions are created, for /, for /home and for swap.
On the / partition the system files are stored (anything else other then /home), and on the /home partition the personal data and settings (instellingen) of the users of the system.
For instance: sda1 for /, sda5 (within sda2 as a container) for /home, and sda6 for swap.
All these partitions may be put on one drive (as in the example), but may also be put on two or more physical drives, such as the system / on a SSD, and /home on a mechanical rotating hard drive.
This way upgrading to a new Ubuntu you only change the contents of /, but not those of /home (don't format /home!!!).

So: What you mean with "using the 14.04 disk as my new /home" is not clear to me, as I already wrote :)

Topsiho

---

### Post by leobos2 on 2015-04-07
> **Topsiho said:**
> Hello leobos2,

I must say that I don't understand what you are trying to tell us with "I wanted to use the 14.04 disk as my new /home".
A typical install of Ubuntu (or other Linux), with a separate /home partition, is that on the hard disk(s) separate (aparte) partitions are created, for /, for /home and for swap.
On the / partition the system files are stored (anything else other then /home), and on the /home partition the personal data and settings (instellingen) of the users of the system.
For instance: sda1 for /, sda5 (within sda2 as a container) for /home, and sda6 for swap.
All these partitions may be put on one drive (as in the example), but may also be put on two or more physical drives, such as the system / on a SSD, and /home on a mechanical rotating hard drive.
This way upgrading to a new Ubuntu you only change the contents of /, but not those of /home (don't format /home!!!).

So: What you mean with "using the 14.04 disk as my new /home" is not clear to me, as I already wrote :)

Topsiho

You're close :-P
I wanted to have all the files plus settings from the 14.04 disk copied to the new 15.04 (because it's shiny) installation. Format the 14.04 disk and put my /home on the 14.04 disk. As it will be easier to install without losing /home like you explained earlier.

@TheFu: Thought so

---

### Post by Topsiho on 2015-04-07
You know, I think, that 15.04 is just an intermediate distribution, which will be supported for only 9 months? I am glad you think 15.04 is shiny, though :)
The LTS-versions, every April in the even years (12.04, 14.04, 16.04 ...) are supported 5 years, but are getting obsolete fast during that time.

Topsiho

---

### Post by TheFu on 2015-04-07
> **Topsiho said:**
> You know, I think, that 15.04 is just an intermediate distribution, which will be supported for only 9 months? I am glad you think 15.04 is shiny, though :)
The LTS-versions, every April in the even years (12.04, 14.04, 16.04 ...) are supported 5 years, but are getting obsolete fast during that time.

Topsiho

I don't think LTS releases are obsolete as long as they are under support.  Had a 10.04 server running here until a few weeks ago. It was rock solid all these years.  Still have a bunch of 12.04 servers running and don't plan to move them for another year at least.

Newer isn't always better for all needs.  Even on my desktop, I probably won't move off 14.04 until 16.04 has been out a few months.  The only programs that tend to cause issues are those tied to social media. Everything else keeps working.

---

### Post by Topsiho on 2015-04-07
That depends, I think, what you/I mean by "obsolete" :)

I agree that newer doesn't always mean better. Or that older versions of applications don't work anymore when there are newer versions.
In a server I think I would leave things as they are (except for updates) as long as possible.
On the desktop I would consider using a newer version of Unity, as it is being developed and getting better.

Obsolete doesn't mean useless, but "there are newer options" to me ...

:)

I am not a native English speaker, so I may be wrong, and may have used the word obsolete in an incorrect manner. If so: sorry :)

When changing to the next LTS-version, it is also my policy to wait until at least the first next point release, before I do so. Even then I found that 14.04.1 was less stable than the fully updated 12.04 that I used.

Topsiho

---

