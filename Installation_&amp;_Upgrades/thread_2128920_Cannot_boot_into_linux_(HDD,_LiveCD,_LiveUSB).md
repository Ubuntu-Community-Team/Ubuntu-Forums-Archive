---
title: "Cannot boot into linux (HDD, LiveCD, LiveUSB)"
date: 2013-03-24
forum: Installation &amp; Upgrades
---

### Post by LittleJakub on 2013-03-24
So, my specs are:

  > [INDENT]   :arrow: Motherboard:   ASRock Z77 Extreme4

      :arrow: CPU Type:   Intel® Core™ i7-3770K CPU @ 3.50GHz

      :arrow: CPU Speed:   3.52 GHz

      :arrow: System Memory:   15.89 GB

      :arrow: Video Card Model: NVIDIA GeForce GTX 670

      :arrow: Video Card Memory:   3.95 GB

 [/INDENT]


 And I've been running Ubuntu 12.04 LTS for a long time on a separate HDD that I had installed just for linux purposes.

  2 days ago I dismantled my PC components, because I was mounting a  new molex 120mm fan in my chasis.

When I put everything back again, I  cannot boot into any kind of linux- my HDD (Windows drives run fine),  when trying to run LiveCD/LiveUSB the options menu pops up (what to do-  if I want to run or try or install Ubuntu, etc.) which means that in my  BIOS I haave USB and CD boot up enabled.

  But what might have happened to cause such an effect- impossible booting into linux? AAnd how can I fix it?

  Please Help!

  Kuba

---

### Post by LittleJakub on 2013-03-25
Please, could anyone help me? I really have no idea what might cause this- Windows 8 one the other HDD runs same as it did before, but Ubuntu simply does not boot into Unity :(

---

### Post by Bashing-om on 2013-03-25
LittleJakub; Hi !

Be advised that Windows 8 introduces factors (UEFI for one) that makes for a whole new ball game. Many of us do not have the background knowledge to deal with it - speaking mostly for myself-.
So, one thing at a time; greatest importance being able to boot the liveCD.
Can you set in bios - I believe through the UEFI boot loader - to boot from the cd device ?

Once the liveCD is booted one can look at the drives on the system, or make some educated guesses as to why they are not seen.
[INDENT=3]
try'n to help

[/INDENT]

---

### Post by oldfred on 2013-03-25
Some Asrock have different ports - Asmedia that have caused issues. When you plugged drives back in did you change to Asmedia port?

From another poster:
>  So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!



Also any sytem wtih i-series Intel chips usually has a motherboard with UEFI/CSM. So how you install Windows whether UEFI or BIOS/legacy/CSM/AHCI is how systems boot. And both need to be in same mode.

---

### Post by LittleJakub on 2013-03-25
And that did the trick!

Just had to move the CD SATA cable from Asmedia SATA ports into Intel ones, and it works back again! Yay!

Thanks guys! :)

---

### Post by Bashing-om on 2013-03-25
LittleJakub;

Pleased that it is sorted out, up and running. oldfred performs again - his infinite store of knowledge !

Please mark the thread as "solved" to aide others seeking solutions;
current method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
Problem still ? -> graphical instruction: ==>[URL="https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"]https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads

[/URL][INDENT=2]'till we meet again

[/INDENT]

---

