---
title: "Trying to save/remember last OS booted with 9.10 (Karmic Koala) and Grub2"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by mdlueck on 2009-12-13
I am trying to set up several computers with dual WinXP / Ubuntu using Ubuntu 9.10 (Karmic Koala).

I am editing the file: /etc/default/grub to specify:

GRUB_DEFAULT=saved

in place of the default GRUB_DEFAULT=0

Then I issue $ sudo update-grub

It appears to do nothing to change the Grub configuration. Booting WinXP, then rebooting, Grub is still set to boot the top menu choice which is the Linux partition.

I recall in the original version of grub, it was necessary to specify "savedefault" for menu choices that it was desirable to when that choice was booted to, save the default choice for the next Grub boot. Is the an equivalent with Grub2 that I just have not read about?

As a work around, it does work to specify the full name of the Windows menu choice, and specifying that as the default results in WinXP being the default. That is the only way I have found to shift the default with Grub2.

I would like it to remember the last OS booted and assume the same as last time at the next time.

Suggestions? TIA!

---

### Post by phillw on 2009-12-13
Hi,

In amongst things you can do to grub2 [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Is this --> [https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries]("https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries")

Now, I'm not totally au-fait with grub2 - you'd want someone like darkod or drs305 to validate my thoughts, but the .40 should allow you to make & keep a boot sequence of your choosing.

You'd be blanking out the .10 and .30 ones - So I'd really caution that you ask one of the guyz more familiar with grub2 to check this theory.

I know you can use chmod -x to hide stuff from Grub2 - That is covered in that community doc, or on drs's thread over at --> [http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305](http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305)

That section also covers this snippet ...

> **Saved**

 
[LIST]
[*]If the default option is set to "saved", the last kernel/system successfully booted will be selected and run if not overridden by the user.
[/LIST]
 
which I believe you were also looking to achieve.

hope that's of help - Grub2 is a pretty darn powerful wee beastie !!

Regards,

Phill.

---

### Post by mdlueck on 2009-12-13
> **phillw said:**
> In amongst things you can do to grub2 [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Excellent, Please see this exact link on the page you mentioned:
[https://help.ubuntu.com/community/Grub2#line-154](https://help.ubuntu.com/community/Grub2#line-154)

I am trying to get the listed "GRUB_DEFAULT=saved" to actually work when booting Windows.

Like I mentioned, I can use "GRUB_DEFAULT='xxxx'" to force it to Windows all of the time. So I know the GRUB_DEFAULT= entry is taking affect somewhat.

> **phillw said:**
> Now, I'm not totally au-fait with grub2 - you'd want someone like darkod or drs305 to validate my thoughts, but the .40 should allow you to make & keep a boot sequence of your choosing.

You'd be blanking out the .10 and .30 ones - So I'd really caution that you ask one of the guyz more familiar with grub2 to check this theory.

That web page does not make it sound so complicated. Was the web page not complete then?

Sincerely,

---

### Post by phillw on 2009-12-13
> **mdlueck said:**
> Excellent, Please see this exact link on the page you mentioned:
[https://help.ubuntu.com/community/Grub2#line-154](https://help.ubuntu.com/community/Grub2#line-154)

I am trying to get the listed "GRUB_DEFAULT=saved" to actually work when booting Windows.

Like I mentioned, I can use "GRUB_DEFAULT='xxxx'" to force it to Windows all of the time. So I know the GRUB_DEFAULT= entry is taking affect somewhat.



That web page does not make it sound so complicated. Was the web page not complete then?

Sincerely,

The community page & Grub2 basics are both complete. The writer of them knows far, far more than me (and most of us) on Grub2

> drs305 >> phillw,

I wrote both my Grub 2 Guide and the community doc.

If anyone can write a good how-to - that gentleman can. The only reason I advise caution is that I am not familiar enough with Grub2 to say my suggestion would
a) work
b) not bork your grub

Although, if you read this --> [http://www.vpolink.com/blog.php?bt=20](http://www.vpolink.com/blog.php?bt=20)  You'll see that his recovery works ;-)

darkod has been heavily involved in Grub2 problems, it was for that reason I advised you 'bounce' my idea off him - he may well be aware of any possible pit-falls.

But, if you've read through those excellent articles, and can see clearly a method to achive what you seek... well, "that's a plan"  - If it borks, recovery is not too difficult.

You'll learn loads doing it, and can't break it too badly.

Regards,

Phill.

---

### Post by mdlueck on 2009-12-13
> **phillw said:**
> ... you'd want someone like darkod or drs305 to validate my thoughts ...

Very well. Then how do I get in touch with them? Or are they also monitoring this forum?

Sincerely,

---

### Post by darkod on 2009-12-14
GRUB_DEFAULT is used to specify which entry in the menu you want as default. I have never seen =saved value to be used. I know you can use either 0,1,2 or the name of the OS as you already found out yourself.

But from your posts I didn't understand what you really want to achieve? If it's only windows to be default entry, you already found that out, using the name is the easiest way, because it still works when adding new kernels with updates. If you use a number like 0,1,2 then the position of windows in the menu changes with adding kernels.
The other option usually used for grub/grub2 is GRUB_TIMEOUT value which controls the seconds waiting before the default entry loads.
Those are the most commonly changed options.
For getting rid of the memtest entries I usually make the file unexecutive with:
sudo chmod -x /etc/grub.d/20_memtest86+

And after doing any changes in grub2 you need to run:
sudo update-grub

If you have any other questions, ask, but my knowledge of grub2 is also limited.

PS. OK, I just reread it myself. Yes, =saved should work to make the last choice as default. Is it not working for you?

---

### Post by mdlueck on 2009-12-14
> **darkod said:**
> PS. OK, I just reread it myself. Yes, =saved should work to make the last choice as default. Is it not working for you?

Greetings darkod-

Yes, that is what I am seeing. I adjusted the value to =saved, ran $ sudo update-grub, boot to Windows, reboot, and Ubuntu (top Grub choice) is still default.

I would like both booting to Linux / Windows to update the saved memory and pick that OS at the next Grub boot.

Sincerely,

---

### Post by darkod on 2009-12-14
> **mdlueck said:**
> Greetings darkod-

Yes, that is what I am seeing. I adjusted the value to =saved, ran $ sudo update-grub, boot to Windows, reboot, and Ubuntu (top Grub choice) is still default.

I would like both booting to Linux / Windows to update the saved memory and pick that OS at the next Grub boot.

Sincerely,

Did you try ="saved"? I know it was without quotes in the instructions, but try it like that too.

---

### Post by phillw on 2009-12-14
BTW, please don't hate me darkod .. ):P

Thanks for popping by.

It is beyond my knowledge of Grub2. ( When's Drs back from Egypt ? - lol)

Phill.

---

### Post by phillw on 2009-12-14
> **mdlueck said:**
> Greetings darkod-

Yes, that is what I am seeing. I adjusted the value to =saved, ran $ sudo update-grub, boot to Windows, reboot, and Ubuntu (top Grub choice) is still default.

I would like both booting to Linux / Windows to update the saved memory and pick that OS at the next Grub boot.

Sincerely,


Ahh, Euston, we *may* have a problem..... Grub has to hand over booting of Win to the Win loader - I suspect that once you say "Go boot Windows", Grub follows its own rules and quietly retires from any further action. Just a thought on the matter .. 
I could (read = probably) be wrong.

Let me go have a try on my system.


Phill.

---

### Post by phillw on 2009-12-14
Hmm. it didn't save my choice of Win as last booted..... However, and next on my list of things to play with is this little snippet..

> 
[LIST]
[*]Custom entries can be added to the *40_custom* file or in a newly created file. Based on its name, *40_custom* entries by default appear at the bottom of the menu. A custom file beginning with *06_* would appear at the top of the menu since its alphanumeric sorting would place it ahead of *10_* through *40_* files. 
[*]

[/LIST]


So, 06_ will always be ahead of any thing else ... Now, it can't update itself as to the last booted OS, but it *seems* like doing a manual entry into .lst from the grub legacy days.

I hope drs305  has enjoyed his well deserved break to Egypt. It'll be nice to have him back, though :D

Phill.

---

### Post by mdlueck on 2009-12-20
> **darkod said:**
> Did you try ="saved"? I know it was without quotes in the instructions, but try it like that too.

I just tried that, same behavior. As if it is set to =0.

Since there is a bit of automagic partition detection with this new Grub, where does one look to see if savedefault is a behavior of a given menu choice?

---

### Post by drs305 on 2009-12-20
> **mdlueck said:**
> I just tried that, same behavior. As if it is set to =0.

Since there is a bit of automagic partition detection with this new Grub, where does one look to see if savedefault is a behavior of a given menu choice?

The entry is stored in /boot/grub/grubenv, but it's not as simple as that.

Warning: Geek alert. You may not wish to read any further.

I played a bit with the "saved" setting when G2 first came out but haven't used it much since, and not with Windows.

After stumbling on this thread about three hours ago, I've been testing the "saved" entry. 

The "saved" string is entered into /boot/grub/grubenv. If you change the default to "saved" and run update-grub, you won't see it immediately. The "saved" entry appears to be updated when a selection is made from the Grub 2 menu.

For Windows, I just entered "saved" as the DEFAULT in /etc/default/grub, ran "sudo update-grub" and booted to Windows. While in Windows, I checked the contents of /boot/grub/grubenv and indeed it contained the Windows title. When I rebooted, Windows was the highlighted entry.

Now a couple of interesting points. If you return to the G2 menu with Windows highlighted and change to Ubuntu, boot, and then check grubenv, it will now show "Ubuntu... " or whatever you just booted to. So the only way you would normally ever *see* the Windows entry in grubenv would be from within Windows (when Windows was the last booted entry).

Secondly, "saved" would be better labeled "lastused" IMO. It is saved only if no other selection is made. If you make another selection from the menu, that item now becomes the "saved" entry.

Another point: You can probably edit grub environment and place the title on the second line, EXACTLY as the string is depicted in grub.cfg (everything between the quotes), [COLOR="Red"]HOWEVER:[/COLOR]: it appears *grubenv* must be exactly 1024 bytes. I've edited and saved it before and it generated an error message on boot saying it was an incorrect size. So if you edit it, it looks like it needs to be exactly 1024 bytes (add or subtract # symbols if not). Fortunately, there is a script to do this for you: **grub-editenv** run as root. 

You can view the current contents with this command:
```
sudo grub-editenv /boot/grub/grubenv list
```
You can create a new, default grubenv file. For me, I have to delete the current /boot/grub/grubenv file before it will create the new one. This will also fix "environment" errors (if you delete the existing file first).
```
sudo grub-editenv /boot/grub/grubenv create
```
To create a new saved default without having to boot into it first:
```
sudo grub-editenv /boot/grub/grubenv set saved_entry="Exact_menuentry_from_grub.cfg"
sudo update-grub
```

One final bit of geekiness: In Grub legacy, the "saved" setting was saved as the DEFAULT number (0,1,2,etc). If a new kernel was added automatically, it became 0 and you would no longer get your old kernel, even if it was "saved".  G2 stores the "saved" value as a string, so even after an update, the older kernel would still be the "saved" one, if though it's position in the menu had dropped down one entry.

Summary 
Here is how it should work:
/etc/default/grub: DEFAULT=saved
sudo update-grub
Boot to Windows
Windows should be highlighted the next time you boot.
It should stay Windows until you select another OS.

Here is what I'd try if "saved" isn't working:
Remove /boot/grub/grubenv
Create a new grubenv (see above)
Add the exact Windows entry to grubenv using the grub-editenv set command (see above).
Update grub.
Reboot.
See if the Windows entry is highlighted.

If you always want to have Windows as the highlighted entry, use the Windows string in the DEFAULT setting of /etc/default/grub.
Example: 
> 
GRUB_DEFAULT="Microsoft Windows XP Home Edition (on /dev/sda1)"

Then update grub.

---

### Post by mdlueck on 2009-12-20
> **drs305 said:**
> For Windows, I just entered "saved" as the DEFAULT in /etc/default/grub, ran "sudo update-grub" and booted to Windows. While in Windows, I checked the contents of /boot/grub/grubenv and indeed it contained the Windows title. When I rebooted, Windows was the highlighted entry.

That is how I want it to work, however that is not how I am seeing it work.

I hand install Windows at the front of the HDD, then install Ubuntu 9.10 beyond Windows on Extended / Logical. Ubuntu adds Windows to the bottom of the Grub menu.

With these settings...

> **drs305 said:**
> Summary
Here is how it should work:
/etc/default/grub: DEFAULT=saved
sudo update-grub
Boot to Windows
Windows should be highlighted the next time you boot.
It should stay Windows until you select another OS.

Linux, the top Grub choice, is still active when Windows reboots.

> **drs305 said:**
> 
If you always want to have Windows as the highlighted entry, use the Windows string in the DEFAULT setting of /etc/default/grub.
Example:
Quote:
GRUB_DEFAULT="Microsoft Windows XP Home Edition (on /dev/sda1)"
Then update grub. 


This does work, and is the workaround I am using since =saved is not working... thus the point of this thread.

I have installed multiple systems with dual XP/Ubuntu, and all systems are working the same (wrong) way.

---

### Post by drs305 on 2009-12-20
> **mdlueck said:**
> That is how I want it to work, however that is not how I am seeing it work.


From within Windows, have you tried to view what's contained in Linux's /boot/grub/grubenv ? At least you can see if grubenv is storing the correct value.

You could also check when the Grub 2 menu appears on a reboot after using Windows, by pressing "c" to get to the command line and then typing:
> cat (hdX,Y)/boot/grub/grubenv
Finding out what value is stored in grubenv might be the first step in determining why it doesn't work for you.

Note: I also know that if I have an improper entry listed as the default in G2 it will also always revert to the top menu item.

---

### Post by mdlueck on 2009-12-20
> **drs305 said:**
> From within Windows, have you tried to view what's contained in Linux's /boot/grub/grubenv ?

How? The /boot partition is an ext4 filesystem.

> **drs305 said:**
> You could also check when the Grub 2 menu appears on a reboot after using Windows, by pressing "c" to get to the command line and then typing:

I will at least try that... that seems doable.

> **drs305 said:**
> Note: I also know that if I have an improper entry listed as the default in G2 it will also always revert to the top menu item.

If it is improper, then the Ubuntu 9.10 installer and/or Grub2 made the mistake.

---

### Post by drs305 on 2009-12-20
As far as reading linux partitions from within Windows, Ext2Fsd is reported by some users to be able to read ext4 partitions.

---

### Post by mdlueck on 2009-12-20
> **drs305 said:**
> You could also check when the Grub 2 menu appears on a reboot after using Windows, by pressing "c" to get to the command line and then typing:

Finding out what value is stored in grubenv might be the first step in determining why it doesn't work for you.

Using this method, the appropriate "Windows XP ..." string is set, throgh the selected menu entry was the top one, Ubuntu Linux.

So at least Grub saved the last OS properly... trouble is picking it from the list at the next boot.

---

### Post by drs305 on 2009-12-20
Just for reference, here are the applicable lines from grub.cfg for my Windows entry, when using "saved". They were copied from within Windows, or you could check with the cat command from the G2 command line before selecting the next OS:

> 
load_env
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
...
...
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ceecff9eecff7f51
	drivemap -s (hd0) ${root}
	chainloader +1
}


And the grubenv first/second lines:
> 
# GRUB Environment Block
saved_entry=Microsoft Windows XP Home Edition (on /dev/sda1)


By the way, I couldn't get Ext2Fsd to read ext4 partitions from Windows.

---

### Post by mdlueck on 2009-12-20
Understood.

Since at the G2 command line the XP entry seems to be correctly indicated, I assume the trouble is in Grub selecting that entry from the list.

---

### Post by mdlueck on 2009-12-26
Thread bump... Any further suggestions?

I had stated that at the Grub prompt, the saved boot choice seems to be WinXP, so the problem must be in Grub handling the saved choice in my opinion. What next...???

---

### Post by mdlueck on 2010-01-06
Since silence persists here, I opened a bug against my findings and referenced this discussion thread. The bug report URL is as follows:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/503935](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/503935)

---

### Post by mdlueck on 2010-01-21
Following up here as well... I tested Lucid Alpha 2 and Grub works as it should. This bug, therefor, is specific to Ubuntu 9.10.

---

