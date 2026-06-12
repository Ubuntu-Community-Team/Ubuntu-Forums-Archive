---
title: "Ub  errr  wi  arghhhh ...not sure,,,wtf"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by kat47 on 2013-06-02
i had xp home,fully updated, drivers in..working.
Installed ubuntu 12.04 ,had to select menu at help screen so i could select nomodeset while running in live mode,after installing ubuntu i had to select safe graphic mode ,then pressed esc, selected resume boot..then a screen would come up saying that i would be leaving safe graphic mode..and ubuntu would then boot as normal.

I hope your following this.

While booted in ubuntu i noticed it wasnt displaying the partion it was installed on..just the windows partion a data partition and the swap file.
Thats strange i thought...

So i thought i would try to boot into windows...no luck...a message came up saying..

[LIST]
[*] 	 		 			:sad: 		
 	
[/LIST]

Windows could not start because the following file is missing..
Windows root </system32/hal.dll
reinstall a copy of the above file.


Ok...booted xp disc....entered repair....but windows does not find my files...so i cant use the restore option...i tried just using the fixmbr at command prompt....it didnt work:confused: 

I KNOW the windows partion is still there because im now in ubuntu live and i can see them.

Could someone please tell me how i can get back in to windows xp:(

---

### Post by Hekabe on 2013-06-02
Knowing almost nothing about Windows internal workings, I'd say you could probably download a copy of hal.dll off the internet and put it in system32 manually using ubuntu.
Unless, of course, you moved the partition. Did you move your Windows partition (probably /dev/sda1) so it's not in front anymore?
Open gparted in ubuntu and take a screenshot of your drive's partition table and post it, if you can.

---

### Post by kat47 on 2013-06-02
Hi Hekabe...thanx for replying..

no i didnt move the partition..and ive taken out ubuntu 12.04...so thats empty partion until i put fresh ubuntu back on...lol.glutten for punishment.

I will have a go at downloading the file and let you know how it goes.

---

### Post by kc-koellein on 2013-09-04
When you say you tried fixmbr at the command prompt and it didn't work... what do you mean "didn't work"? What error did it throw?

do it again and try fixboot

I just did this last night, btw.

Old hp Pavillion a720n with an XP Home restore partition that would restore the whole machine to factory spec. Wanted a nostalgia machine. So this fixed it, then I worked in XP Home for a while and then installed a dual-boot of Xubuntu. workin' fine.

---

### Post by vasa1 on 2013-09-04
@ kc-koellin, Why don't you start a thread of your own? Why did you decide to post in a thread titled "Ub errr wi arghhhh ...not sure,,,wtf"?

---

