---
title: "reset system in top left of screen of ideapad 1"
date: 2022-09-14
forum: Installation &amp; Upgrades
---

### Post by booshankles on 2022-09-14
I'm just following what boot repair says to do, here isthis this link  [https://paste.ubuntu.com/p/wZF3xPxGYN/](https://paste.ubuntu.com/p/wZF3xPxGYN/)

im just trying to get ubuntu installed on a ideapad 1 using a 64gb microsd card formatted as exfat

---

### Post by tea for one on 2022-09-15
> reset system in top left of screen of ideapad 1
I'm not at all sure which screen you are describing?
Can you supply an image?

I assume that, after a successful installation, Ubuntu fails to boot?

Can you double-check the following in your UEFI Set Up:-
Security > Intel Platform Trust technology > Disabled
Security > Intel SGX > Software Controlled and Disabled
Security > Secure Boot > Disabled (Boot-repair report states disabled but worth checking)
Boot > Boot Mode > UEFI

---

### Post by booshankles on 2022-09-15
Well a few things One because of how quick it would flash by I'm not able to get a picture of it in time but it would pop up real quick saying reset system. 2. Intel platform trust technology and Intel SGX after disabling them both I can now say successfully without needing the bootable USB I am able to successfully normally boot into Ubuntu so thank you kindly because I've been scouring the web for about four or five hours now lol

---

### Post by tea for one on 2022-09-15
> **booshankles said:**
> I can now say successfully without needing the bootable USB I am able to successfully normally boot into Ubuntu

Good news - pleased to have helped.
In order to help other forum members/searchers, it is a nice gesture to mark the thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

