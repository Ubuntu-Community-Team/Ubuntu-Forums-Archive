---
title: "Samsung NP300E5C-S01PL Epic Fail - Destroyed BIOS NVRAM and System - What should i do"
date: 2015-12-07
forum: Installation &amp; Upgrades
---

### Post by D_K_Darna on 2015-12-07
[COLOR=#111111][FONT=Ubuntu] try to describe problem from start
I installed a Lubuntu installation over my NP300E5C I was enjoying it and it was a very good system for me - but i managed to mess a lot of packets and depencies and i wanted to make simple reinstall for another Ubuntu or Dual-boot with Win installation
Then i discovered famous NVRAM broke bug by UEFI in few samsung models - Still at that moment i had at least working Bootable Lubuntu - where i just had problems to installing packets
Still i was careless and not fixed that asap - and i gone to moment where i tottaly broke Lubuntu OS i had on HDD - i couldn't install any package or even execute almost any command .... Dunno why i formated the drive and now im tottaly lost position.....
Only thing i now i am able to do is use a something like Boot Menu of samsung - it looks like booting before BIOS or any OS
It have option to change pad by [TAB] button to App Menu Only option is to choose Ubuntu option in boot menu - it make's screen flickers and show boot Menu again - or sometimes it make PC turn off and reset by itself and whole sequence goes from start
[http://imgur.com/a/6bFmf](http://imgur.com/a/6bFmf) - Album with pcs
I tried many fixes i finished on trying to burn WINPe on Cd and use F3 Failed
I did not dissembled whole laptop to remove bios battery - is there even point in doing it?? Can anyobdy give me a tip how to fix??? I have feeling it's normally fixable but i miss something
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Fresh booting sequence is also very strange - at begging screen light up but still black - stays lit for 3-4 secs turn off and after 2 secs device reboots itself - then i see bios first time ( it "reacts" for function key - i mean pressing F2 change the title on bootom of screen onto "Setup loading..... or bios loading something like this" ) but still it won't load just this stupid menu



[TABLE="width: 660"]
[TR="class: comment"]
[TD="class: comment-text"]I broken my bios by installing Lubuntu over Win7 that was fabric on laptop thanks to this[anandtech.com/show/6713/…]("http://www.anandtech.com/show/6713/samsung-laptops-bricked-by-booting-linux-using-uefi") --- i didn't care and i was normally using Lubuntu. Now Lubuntu i had broken and i can't install other OS cuz im stuck in this menu - [imgur.com/a/6bFmf]("http://imgur.com/a/6bFmf") - Album with pcs..... Can't go into bios - and menu goes also to nowhere ......... I tried 1 : Installing various systems on other Device on HDD and trying to boot somehow laptop to make it in state to fix bios at least ( no sucess




[TABLE="width: 660"]
[TR="class: comment"]
[TD="class: comment-text"]2 : WinPE bootable CD and pressing F3 [Found there ["]askubuntu.com/questions/506322/…]("http://askubuntu.com/questions/506322/cant-enter-bios-settings-after-installing-ubuntu-samsung-np300e5s/506334#506334) - now im stuck and asking you guys for help! Thanks for intresting
[/TD]
[/TR]
[/TABLE]

[/TD]
[/TR]
[TR="class: comment"]
[TD]


Any advices ??? I do care about this laptop it was great and served me well

If theres way to fix it- i want to try[/TD]
[TD="class: comment-text"][/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR]

---

### Post by Rex Bouwense on 2015-12-07
Hi D_K_Darna and welcome to the Ubuntu forums.  
I am not sure if you understand that all of the people here are volunteers and many have jobs and a family life so if your question does not get answered right away perhaps the people that can provide a solution are not on line at the moment.  Please have a little patience.  Bumping your thread probably does more harm than good because many people look for threads with no responses.

---

### Post by D_K_Darna on 2015-12-07
> **Rex Bouwense said:**
> Hi D_K_Darna and welcome to the Ubuntu forums.  
I am not sure if you understand that all of the people here are volunteers and many have jobs and a family life so if your question does not get answered right away perhaps the people that can provide a solution are not on line at the moment.  Please have a little patience.  Bumping your thread probably does more harm than good because many people look for threads with no responses.
Of course i understand that very well :)

Apologize for my rude behaviour

Just situtation is for me little tight and i would llike to know if this is fixable and worth fixing in next few days.
Or i just should get over it and buy new one :)




Peace brother and thanks for getting me straight - sorry again

---

### Post by matt_symes on 2015-12-07
Hi

From the article you linked

Have you tried this ?

> Update: It appears the problem stems from NVRAM corruption. Removing power, opening the laptop up, and disconnecting the CMOS battery appears like it will clear the problem, but that's a pretty serious set of steps to take for most laptops.

Also in the same article

> Long-term, we expect Samsung to release BIOS and firmware updates for the affected laptops, though how long that might take is unknown. **Short-term, the workaround is for Linux to boot these Samsung models using the Compatibility Support Module (CSM), which basically bypasses the UEFI bootloader, but dual-booting via CSM appears to be a bit complex.** Ubuntu’s development team has worked with Samsung and identified the kernel’s Samsung-laptop driver as the prime suspect, and there are other workarounds proposed already to address the issue. However, these fixes have not yet been merged into the main Linux development tree, so again we recommend Samsung laptop owners who use Linux exercise caution.


Kind regards

---

