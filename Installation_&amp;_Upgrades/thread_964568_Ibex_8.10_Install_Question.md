---
title: "Ibex 8.10 Install Question"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by PrinceArithon on 2008-10-31
As usual when upgrading from one version of Ubuntu to another there is a possibility of something messing up that worked before.  As I'm reading it seems people are having nvidia problems which usually happens on these upgrades.

This time...after 2 years of using and upgrading Ubuntu, I'm wondering about just wiping my Ubuntu partition clean and just reinstalling.  I've read a few times about people doing this and they all seemed to say everything worked fine after the installation, and not upgrade.

So I'm just wondering if that is the case this time.  So could anyone who wiped their partition clean and then did a fresh install of 8.10 tell me how it went for them??  Because if it did the same as the upgrade did then I would rather just do the upgrade as it's easier than wiping the partition clean...

Sorry for the weird question.  I just wanted to try something new to see if it was a better way.

---

### Post by Ng Oon-Ee on 2008-10-31
I have a separate /home partition, so for me it was a no-brainer, just clean install and re-use the same /home partition. The only thing I had to do at the start was chown my old home partition to my new UID.

Everything works just like in Hardy, except my laptop can now hibernate reliably =)

---

### Post by PrinceArithon on 2008-10-31
Nice.  OK that sounds exactly like what I'm going to do then.  Thank you.

---

### Post by kstella on 2008-11-26
> **Ng Oon-Ee said:**
> I have a separate /home partition, so for me it was a no-brainer, just clean install and re-use the same /home partition. The only thing I had to do at the start was chown my old home partition to my new UID.

Everything works just like in Hardy, except my laptop can now hibernate reliably =)

Hey, can you give us details on how you did that? I also have a separate /home partition and am worried about accidentally erasing it or breaking something when I clean install.

Thanks.

---

### Post by cjazz on 2008-11-27
> **Ng Oon-Ee said:**
> I have a separate /home partition, so for me it was a no-brainer, just clean install and re-use the same /home partition. The only thing I had to do at the start was chown my old home partition to my new UID.

Everything works just like in Hardy, except my laptop can now hibernate reliably =)

And I've had much the same experience, except no need to chown my old home partition. Everytime I reinstall, I take the manual option when it comes to partition, redesignate my old home partition as /home, and make sure I don't format it. If I keep the same user name, things work fine.

---

