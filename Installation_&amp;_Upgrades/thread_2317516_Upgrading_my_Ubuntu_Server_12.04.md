---
title: "Upgrading my Ubuntu Server 12.04"
date: 2016-03-17
forum: Installation &amp; Upgrades
---

### Post by ReFike on 2016-03-17
Hey, 

I have rig with Ubuntu 12.04.5 LTS 32bit Server edition. As we know this release is supported until April 2017.
When I login it says: 
      ```
 [FONT=monospace][COLOR=#000000]New release '14.04.1 LTS' available. [/COLOR]
Run 'do-release-upgrade' to upgrade to it.[/FONT]
```   
[B]Ubuntu Server 16.04 LTS is around the corner, what will happen when 16.04 will be released?
The 'do-release-upgrade' will upgrade my 12.04 to 14.04 or 16.04? [/B]
I dont really want to upgrade my 12.04 to 14.04 in this year, but if I cant upgrade to 14.04 after 16.04 released 
then I have to upgrade to 14.04 in this month.

---

### Post by grahammechanical on 2016-03-17
Server or desktop it makes no difference. We upgrade from LTS to LTS to LTS. Or to put it another way, 12.04 to 14.04 to 16.04. Ubuntu 14.04 has an even longer amount of support left than 12.04. So, you will still be able to upgrade to 14.04 after 16.04 has been released. In fact the only way anyone on 12.04 can move on to 16.04 is to first upgrade to 14.04. That is the process.

Of course, we can bypass this upgrade process by doing a fresh install of 16.04. And it is also true that life becomes more difficult if we delay upgrading until after our version has reached end of life. That is espeically true with interim versions.

Regards.

---

### Post by ReFike on 2016-03-17
Thanks for the answer, good to know this. I will only upgrade in early 2017 to 14.04. My only concern to upgrade to 16.04 is the fact that I have limited storage space on my rig and upgrades usually needs hundreds of MBs, maybe in the future I will have another rig with more storage space. As I know upgrading from 12.04 to 14.04 takes about 4-500MB free space.

---

### Post by Markus_Lankeit on 2016-06-09
So I did this... I had 12.04, and upgraded to 14.04.  Now, when I do "sudo do-release-upgrade", I get:

> Checking for a new Ubuntu release
No new release found


Huh?  Why doesn't 16.04 show up as a valid upgrade when I just finished the 14.04 upgrade?  I'm sure glad I'm testing this on non-production systems.

Seems like a straight 16.04 load would be much quicker.  It would still be a bunch of work, but at least I can finish the same day.  Plus, I can swap boot disks and have a fall-back just in case of murphy's fubar. 

-ml

---

### Post by Impavidus on 2016-06-09
The upgrade from 14.04 to 16.04 will only be offered after the release of 16.04.1, scheduled for 21 July.

---

### Post by QLee on 2016-06-09
> **Markus_Lankeit said:**
> Huh?  Why doesn't 16.04 show up as a valid upgrade when I just finished the 14.04 upgrade?  I'm sure glad I'm testing this on non-production systems.

I suggest to you that as a system administrator, it would be a wise policy to read the release notes for a release previous to attempting upgrade and I think that good advice regardless of using a non-production, test, system which is also a wise practice. If your upgrade hadn't gone well, nothing but testing time would have been lost. Generally, those using an LTS release for production are not early adopters because they want stability.

If you had read the 16.04 telease notes you would not have had to ask your question. In addition, there may have been some known possible problems that you would have been warned of. For example: if your test system was using the fglrx driver at the time of upgrade and others.
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

I don't mean this to be "scolding" you (you set a good example), but others reading this may be able to develop appropriate practices if they see things spelled out and find practices that make sense to them and that they want to adopt.

---

### Post by Markus_Lankeit on 2016-06-09
Impavidus: Thx for the clarification!

QLee: I was thrown off by grahammechanical's response... Thx for the note re: release notes--I'll RTM going forward.  As a general side-note, I loaded 16.04 clean on a new system, and it is working well for me (I had all sorts of samba issues with 14.04).  I do have a number of systems still at 12.04, and was hoping to get these to 16.04, hence my test.   

[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721")

---

### Post by QLee on 2016-06-09
Markus, you are quite welcome. I imagine everyone answering in this thread feels that way, otherwise they wouldn't be here answering. 

A small mistake though, it's generally considered inappropriate to add a question to someone else's question thread. I realise it did seem a good place to start since the title was exactly what you wanted to ask about but these forums prefer that a new question starts a new question thread. (within reason and as you can see, you got answers anyway) 

If you had started this thread then you would have been able to mark it solved and thus make it a bit more valuable in the data base. Sometimes people only search for solved threads. The Search field at the top of the forum can find a lot of answers about Ubuntu quickly if using sane keywords.

I also have a bare metal install of 16.04 for learning about the new "features" (some I like some not so much), I'm waiting until after the first point release to try an update.

---

