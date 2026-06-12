---
title: "Golly, wouldn't it be great if Grub2 booted my computer ?"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by budword on 2010-03-28
I read in the Grub2 guide about all the great improvements of Grub2 over Grub. Thats great. Unfortunately, Grub2 won't boot my laptop, while Grub managed to boot the laptop just fine. I'm sure all those great features matter to someone, if Grub2 won't boot the computer at all. 

With Grub, I could edit menu.lst and the changes would stick around. Now we have grub.cfg, which we can't edit at all to fix something that's broken. Now we do have 5 or 6 other files we can edit, and hope grub.cfg grabs the right bit and puts it in the right spot, but it doesn't. 

Here is my issue. Grub2, via the uneditable grub.cfg, puts a lovely line option in that starts with "search". If that line is there, I can't boot my laptop, because evidently grub is searching for a device that isn't there. If I press "e" during boot, I can edit that line out on the fly, and the laptop will magically boot, just fine. However, I prefer to not be forced to do that every time.  Ok, this is Linux, I'll just edit the grub.lst file to make sure grub isn't using that line to boot the computer. Opps. Can't anymore.

If I wanted to be told which files I can edit and which I can't, I'd fricking use Windows or OSX. 

Now, I've discovered I can't edit grub.cfg. I can edit the 40_custom file, which sure is great. However, this doesn't fix the problem, as it seems to just add entries that grub.cfg adds on the fly. 

There is also a /usr/sbin/grub-mkconfig file that grub.cfg consults to create the fantastic non working, non editable grub that I am now blessed with, but I can't fricking edit that either. 

Does lilo still work ? Because last I remember, lilo could manage to boot my computer, and when it was messed up, I could edit it to make things work. 

How about just grub ? I could edit that to make it work too. 

Now I'm sure all the improvements to grub2 are just fantastic, but if you can't edit out options that break stuff, it just plain doesn't matter. 

If I have to put up with someone else deciding what file I can and can not edit on my own damn computer, I might as well just buy a mac. 

If anyone can tell me how to get grub2 to not boot that option, it might stop me from becoming violent with my laptop.

Thanks much...

David

---

### Post by drs305 on 2010-03-28
> **budword said:**
> 
There is also a /usr/sbin/grub-mkconfig_lib file that grub.cfg consults to create the fantastic non working, non editable grub that I am now blessed with, but I can't fricking edit that either. 

David

budword,

Welcome to Ubuntu and the Ubuntu forums.

You will find help here. We understand your frustrations but we generally try to take a more positive approach.

You can in fact edit grub-mkconfig_lib, you just have to do it as root. I'll provide the way to remove the search line, which will at least move your problem down the road a bit.

Open grub-mkconfig_lib for editing:
```
gksu gedit  +135  /usr/lib/grub/grub-mkconfig_lib
```

Find this section of the file, around line 135 (which is where gedit should open):
> 
  # If there's a filesystem UUID that GRUB is capable of identifying, use it;
  # otherwise set root as per value in device.map.
echo "set root='`${grub_probe} --device ${device} --target=drive`'"
**[COLOR="Red"]#[/COLOR]**  if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
**[COLOR="Red"]#[/COLOR]**    echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
**[COLOR="Red"]#[/COLOR]**  fi


There was a time when the "--no-floppy" section of the search line was causing problems. If you can simply edit out the "--no-floppy" section of the search line and get your system to boot from the Grub 2 menu, you can keep the entire section above and just remove the "--no-floppy" entry without adding any of the comment (#) symbols.

---

### Post by budword on 2010-03-28
Thanks for your help drs305. Frustration doesn't not even describe it. They took something simple that worked just fine and broke it. Instead of having all the info  you need in menu.lst, they not only created a grub.cfg that you can't edit or fix, but generated it from a /usr/sbin/grub-mkconfig file, that you can't edit or fix, that itself grabs entries from /usr/lib/grub/grub-mkconfig_lib. Not to mention confusing the matter with a 40_custom file.

How can that possibly make sense to someone ?

Well, ranting over now I guess. Thank you for your help drs305, I have it fixed now. So, to fix grub.cfg, you don't edit /usr/sbin/grub-mkconfig, where it pulls it's entries from, you do edit /usr/lib/grub/grub-mkconfig_lib, where evidently /usr/sbin/grub-mkconfig pulls it's info from, just to pass it on to /boot/grub/grub.cfg, as long as you remember to run "sudo update-grub". And here you thought it might be complex or not make any sense. 

Silly rabbit.

Just for anyone else who has this same issue, remember to run "sudo update-grub" or your changes won't go through. 

Oh, I've googled quite a bit to track down and solve this issue, evidently it's fairly common with thinkpads, at least for 9.10. Maybe it'll be fixed with 4.10. 

Thanks much....

---

### Post by drs305 on 2010-03-28
Glad you've got things working now. I think I overwrote the update-grub instructions when I added the paragraph about "--no-floppies". 

When the grub package (as opposed to the routine 'update-grub') gets updated you will probably have to run the fix again - although at some point maybe the issue will be fixed for your system. You will know it's time to edit the file if you are presented with a choice of "accept the maintainer's version" during a grub update.

If you wouldn't mind, if you have no other questions on the issue at hand, please mark the thread solved via the "Thread Tools" link at the upper right of the first post. It helps the "helpers" know which posts to concentrate on and lets others know a solution is to be found within the thread. Threads can also have the SOLVED tag removed from the same link should that become necessary.

---

