---
title: "stability 9.10"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by grip82 on 2010-01-25
I've been using ubuntu for a few years now. In the beginning there were always some small problems which annoyed be but lately, ubuntu has been great for me. I've been running 9.10 for a while and even though it didn't feel as stable to me as 9.04 (for example, eclipse was broken), it was fine.

But now I've bought new hardware and did a fresh install of 9.10, this time the 64bit version. It was like being launched, not to beta, but to alpha-land. Is this because this is the 64bit version (which I haven't used in a while), or is it because it's 9.10 ?

A few examples:
- Huge memory leak. Just after boot, my system uses 400mb RAM. When I open my taskmanager, I see this increasing in no time to 1GB, and after an hour or so it's at 3GB. If I scroll up and down in firefox, it costs me 4mb. I already got it to consume all my RAM memory, and it completely killed my computer after a couple of hours. 
- Write speeds on ext4 when using mysql. One word: super-slow. I think I can do it faster by pouncing cards. 
- Video driver crash, screen flipped out, end of story, reboot.
- Flash crashes at least once every 30min.
- (I can go on) ...

I'm not searching for answers for these specific problems. In fact, I found most with google. I was just wondering if 9.10 is known for these stability issues? Or is this because of the 64bit version? I know you can tweak everything and trace memory leaks, and recompile libs and format your drive to ext3 but my time is limited and every hour spent configuring my OS is an hour less development. :)

---

### Post by phillw on 2010-01-25
Hi,

Hmmm, sounds like a very unhappy computer. Whilst not the solution you're looking for - that, as you say, can come with digging around and tracing - given time, which you don't have a lot of.

May I suggest that you partition up and pop on the 32 Bit version of 9.10 and the apps - That should, at least, keep you running without massive memory leak you are experiencing. Leave the 64 Bit one there & as you get time, you can sort out the issue(s) you have with it.

Having a /home partition, if you do not already have one - is very handy for this sort of thing -- [Create a separate home partition in Ubuntu]("http://www.psychocats.net/ubuntu/separatehome")

If you use tasksel to put on your LAMP environement & phpmyadmin, the installtion is quite painless & quick --> [http://www.vpolink.com/threads/493-LAMP-Important](http://www.vpolink.com/threads/493-LAMP-Important)

A simple dump of you MySQL dbase(s) to your /home directory and import into the 32Bit area is also quite painless & will allow you to keep the two sync'd up (I use that system to update the server from my home LAMP installation).

```
mysqldump -u username -ppassword database_name > /home/FILE.sql 
```To Export and 

```
mysql -u username -ppassword database_name < /home/FILE.sql
```To Import

You will have to set up the blank database names to do the import - but they require no structure. 

You will have to set up extra user permissions for the database(s) - unless you fancy trying to take the information_schema, mysql & phpmyadmin over. That may work, but I've never tried it !!

Hope that is of some help.

Regards,

Phill.

---

### Post by grip82 on 2010-01-25
Thanks for the feedback! I hadn't heard of the tasksel yet. I will try it out.

However, I do manage to install an AMP pretty quickly on my machine, including rewrite_mod , importing databases and xdebug and Eclipse + PDT environment to get me going. That's one of the things that I love about ubuntu. If I try this on a WIN box, it is almost considered a daytime task :D

I've had a seperate home partition for a while, but what bothered me was the cluttering up with all these ".program-settings" hidden folders. After a few years, there were many programs I didn't use anymore, but they all had their configs spread through my home directory. So now I have a seperate partition (hard drive in fact) for all my big data, and whenever I install a new version of ubuntu, I copy paste the folders I use from the home directory to the hard drive and start from scratch.

I'll reinstall 9.10 32bit with ext3, if the memory leak is solved, I can handle the rest until 10.04 comes out, which should be a LTS if I'm not mistaken. I think I'll stay with that release for a while :-)

---

### Post by phillw on 2010-01-25
> **grip82 said:**
> Thanks for the feedback! I hadn't heard of the tasksel yet. I will try it out.

I'll reinstall 9.10 32bit with ext3, if the memory leak is solved, I can handle the rest until 10.04 comes out, which should be a LTS if I'm not mistaken. I think I'll stay with that release for a while :-)

Hi it's worth having a look at tasksel, because under 10.04, it's got all sorts of lovely things ready to play with (like cloud computing) - I have ext4 on both my 9.10 and 10.04 set-ups and have had no lag issues on either with MySQL, although I do only have about 1,500 records on the dbase.

10.04 is, indeed an LTS - and whilst still only at alpha2 is quite awesome. The usual graphics driver problems, but stability wise .. Very good. I, also, will be staying with 10.04 as my production machine. The existing 9.10 will become a 'play' area for testing 10.10 out on. 

You can see where 10.04 is up to over on this forum --> [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Once you're happy with no memory leakage, you can easily switch from ext3 to ext4 --> [http://www.vpolink.com/threads/573-Upgrade-ext3-ext4](http://www.vpolink.com/threads/573-Upgrade-ext3-ext4)

Regards,

Phill.

---

### Post by grip82 on 2010-01-25
> **phillw said:**
>  ...

10.04 is, indeed an LTS - and whilst still only at alpha2 is quite awesome. The usual graphics driver problems, but stability wise .. Very good. I, also, will be staying with 10.04 as my production machine. The existing 9.10 will become a 'play' area for testing 10.10 out on. 

You can see where 10.04 is up to over on this forum --> [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Once you're happy with no memory leakage, you can easily switch from ext3 to ext4 --> [http://www.vpolink.com/threads/573-Upgrade-ext3-ext4](http://www.vpolink.com/threads/573-Upgrade-ext3-ext4)

Regards,

Phill.

Cool. You're putting lots of effort in ubuntu, as an alpha tester and by writing these easy-to-follow tutorials. You're really giving something back to the community. It's a shame actually that I haven't. I guess I don't put lots of time in my OS. However, I always run around at work with my ubuntu mug, and I'm always defending the FOSS community against ignorant colleagues ("it's free, so it's fun to play around. Don't expect any serious results").

---

### Post by gachora on 2010-02-18
I was very eager to upgrade from 9.04 to 9.10 but my media player had issues and often failed when running several applications so I reverted to 9.04 which I am not sure I will dump soon unless 10.04 proves me wrong. 9.04 for me beats 9.10 9/10 but guess I haven't had time to tinker with what could have stabilized 9.10 for my laptop. But am for Ubuntu for good!

---

