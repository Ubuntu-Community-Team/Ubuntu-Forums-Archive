---
title: "Use same home partition with jaunty and karmic dual boot."
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2009-09-23
Hi All,

I want to partition my hard drive as follows.

10GB Junaty Root
10GB Karmic Root
4 GB /Swap
Remaining /Home Partition.

So, i want to use same home & swap partition for both Jaunty and karmic. Is it possible? Is it a good idea?

Please comment-
SK

---

### Post by Nickedynick on 2009-09-23
I have a very similar setup on my PC, except with a Windows 7 partition too. It seems to work well for me, but you should note that some settings cause conflicts between the two systems. Nothing serious, but I've found the odd menu or panel item disappearing occasionally when packages get updated.

Edit: Also, Karmic uses GRUB 2 so you should decide before installing which version of GRUB you want to use.

---

### Post by donniezazen on 2009-09-23
> **Nickedynick said:**
> I have a very similar setup on my PC, except with a Windows 7 partition too. It seems to work well for me, but you should note that some settings cause conflicts between the two systems. Nothing serious, but I've found the odd menu or panel item disappearing occasionally when packages get updated.

Edit: Also, Karmic uses GRUB 2 so you should decide before installing which version of GRUB you want to use.

Thanks.

I too have a windows partition. I did not mention it as it is separate and does not have any stake. I rarely use it.

I will be using Karmic most of the time, so, i should not have any problem with Jaunty. 

Thanks.

---

### Post by HankB on 2009-09-23
It is certainly possible. You just need to specify the same partition as /home on either installation. You can even change that (if you do like I did and forget to do that during installation) by modifying the /etc/fstab file to include the home directory. (Note, I had a separate /home partition for my Jaunty install so I simply copied the line from the /etc/fstab in the Jaunty installation to the corresponding file on the Karmic install.)

FWIW, I have Jaunty installed on the 4GB SSD on my Eee PC 901 and /home on the 16GB SSD. I have Karmic installed on a 4GB partition on an 8GB SDHC card.

I can't say whether this si a good idea or not. It seems possible that a newer application from Karmic could modify config files in your home directory to make them incompatible with the older application on Jaunty.

There also exists the possibility that a bug in Karmic could trash your drives - affecting your /home or even the Jaunty root partition.

Backups mitigate either of these risks. In my case, this is a secondary machine so having it trashed would not be a huge problem for me.

HTH,
hank

---

### Post by donniezazen on 2009-09-23
> **HankB said:**
> It is certainly possible. You just need to specify the same partition as /home on either installation. You can even change that (if you do like I did and forget to do that during installation) by modifying the /etc/fstab file to include the home directory. (Note, I had a separate /home partition for my Jaunty install so I simply copied the line from the /etc/fstab in the Jaunty installation to the corresponding file on the Karmic install.)

FWIW, I have Jaunty installed on the 4GB SSD on my Eee PC 901 and /home on the 16GB SSD. I have Karmic installed on a 4GB partition on an 8GB SDHC card.

I can't say whether this si a good idea or not. It seems possible that a newer application from Karmic could modify config files in your home directory to make them incompatible with the older application on Jaunty.

There also exists the possibility that a bug in Karmic could trash your drives - affecting your /home or even the Jaunty root partition.

Backups mitigate either of these risks. In my case, this is a secondary machine so having it trashed would not be a huge problem for me.


HTH,
hank

Thanks, I am not going to run the Jaunty very often. In fact i am going to use it only in case Karmic fails.

I am going to install Jaunty first and then Karmic later so that all the settings of Karmic over rides jaunty settings.
 
What happens when an older version of a software in installed in Jaunty and latest in Karmic? Do they conflict? Whats the result?

Thanks,
SK

---

### Post by Nickedynick on 2009-09-23
It will depend very much on what the specific application is, and whether it maintains support for reading old settings. In theory it could be a disaster, but as I say I've not come across any showstopping errors specific to my setup :)

---

### Post by donniezazen on 2009-09-23
Thanks

Let me try it.

---

### Post by ranch hand on 2009-09-23
If you make sure to use a different user name for 9.04 and 9.10 you should not run into too much problem.

Grub is installed on the root partition along with all your other programs and kernals so you should be able to have grub-legacy to foll back on if you have any grub2 problems.

Grub2 will be installed when you install 9.10 last.  You should have no problem with it.  If you do not have 9.04 on the menu when you reboot from installing, run;
```

sudo update-grub

```
in your terminal and that should fix it right up.

Have FUN.

---

### Post by donniezazen on 2009-09-23
> **ranch hand said:**
> If you make sure to use a different user name for 9.04 and 9.10 you should not run into too much problem.



Thanks a lot for advice. Sorry for the dumb question. What happens when you use two different user name? Will i have access to same home folder if i use two different user name?

Thanks again.

---

### Post by ranch hand on 2009-09-23
Yes but the files, data and configuration, will be under different users.  To have complete, instant access you will have to get into your users permissions and add the users to the respective files.  You really should have access through nautilus anyway.

This should however keep the problems to a minimum as far as your config files go.  If you use the same user name on both you will be getting conflicting configuration from configuring Jaunty and Karmic.  With two separate users this will not happen, at least in theory.  Karmic is an alpha so there may be some leakage due to funky files.

Sounds like an interesting way to do things, I am not sure I have the guts to do it with a stable and an unstable OS.

HAVE FUN.

---

### Post by solitaire on 2009-09-23
although i've not went the "full hog" and used my Jaunty /Home for my Karmic install I HAVE used "ln" to create links to certain folders like ".mozilla-thunderbird" so my Karmic /home has a link pointing to the Jaunty's /home location for thunderbird. saves in reentering all those passwords and server info for a alpha install (I can still access my emails while working without getting the 2 install out of synch ^_^

I'll wait till the beta before thinking about using Karmic as my main OS... (been meaning to do a full reinstall anyway)

---

