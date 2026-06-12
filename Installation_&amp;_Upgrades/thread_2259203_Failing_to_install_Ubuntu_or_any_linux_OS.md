---
title: "Failing to install Ubuntu or any linux OS"
date: 2015-01-02
forum: Installation &amp; Upgrades
---

### Post by RasheedSaeed on 2015-01-02
Over the past few months I have been unable to install any linux systems on my laptop: Ubuntu, Xubuntu, and Lubuntu. The same problem occours during the installation: it suddenly freezes. I have installed them all using a USB with different software applications. My computer is compatible because I have previously owned Ubuntu.

---

### Post by austin_hawkins on 2015-01-02
what type of freeze are you experiencing, screnshots would help

---

### Post by RasheedSaeed on 2015-01-02
> **austin_hawkins said:**
> what type of freeze are you experiencing, screnshots would help

It's a literal freeze. When installing Ubuntu the **dots **changing colour (to show progress of the installation) do not change; when installing Xubuntu, the rotating circle will stop rotating.

---

### Post by Bucky Ball on 2015-01-02
Welcome. When you boot from the install media, in your case USB, and get to the 'Try Ubuntu' 'Install Ubuntu' options, hit F6 and choose 'nomodeset' from the pop-up menu that appears. Proceed. Any different?

Smells like graphics issue so you possibly aren't doing anything wrong with how you're creating the install media. 

We dig deeper. :-k

---

### Post by RasheedSaeed on 2015-01-02
> **Bucky Ball said:**
> Welcome. When you boot from the install media, in your case USB, and get to the 'Try Ubuntu' 'Install Ubuntu' options, hit F6 and choose 'nomodeset' from the pop-up menu that appears. Proceed. Any different?

Smells like graphics issue so you possibly aren't doing anything wrong with how you're creating the install media. 

We dig deeper. :-k

Thank you. Unfortunately F6 did not work, but fortunately I was able to enter a command. However, despite that particular hurdle, the issue still remains.

I have just selected the "disk defects" option and there are no errors.

---

### Post by oldfred on 2015-01-04
What brand/model laptop?
RAM, cpu & video card?

Some need nomodeset and other settings in addition or different video parameters if just Intel chip.

---

### Post by MAFoElffen on 2015-01-04
What would help others to be able to help you is to at least let them know what hardware you are trying to install on. You said "laptop." That could be openly interpretted to mean a wide array of differing hardware.

-What is the brand and model? This would help other at a minimum, to let them look into that specific laptop's specs... What CPU it may have. How much RAM it came with and what it may be upgraded to. What video GPU it may have, to figure out what kernel option it may need. What network devices it may have.
- Where in the install it freezes at. There is a lot of places it may freeze at... "In the install..." is fairly broad in nature. What did it say it did? (There is a status line with messaging at the bottom)... Because it may be that it has no networking, so is freezing when trying to get a package... or it may be that it is freezing when trying to probe hardware...

What oldfred is suggesting is usually standard. Try a LiveCD and see if it runs without problems. You may have to supply some answers to my above to do that well... but If it can't run a LiveCD with help from us, then there's no use to try to install with those problems unresolved, right? 

Please do not have these people try to guess. Help them to help you.

---

