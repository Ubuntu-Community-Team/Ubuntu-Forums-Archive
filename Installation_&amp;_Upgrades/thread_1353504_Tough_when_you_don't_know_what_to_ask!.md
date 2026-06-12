---
title: "Tough when you don't know what to ask!"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2009-12-12
I installed Karmic about 30 days ago. This was a clean install after using GParted (in LiveCD) to change my FS from ext3 to ext4. GParted reported no errors. I used a Karmic "Desktop" CD and ran the install after checking the MD5. The install reported no errors. I use a separate /home via Psychocats.

After many problems unresolved, I backed it all up (again), and did another clean install using the same, proven, CD. The install went well and reported no problems.

I have an MSI GeForce FX 5600 graphics card (8X-AGP & 128 Meg of ram). I did not load the proprietary nvidia drivers first, concentrating on getting the Medibuntu working. All the /home was safely stored on an external usb drive. I could not get Medibuntu working. I could not install Adobe Reader, Google Earth, or Picasa. 

Upon the death of a relative this week, I had to restore the /home as legal docs were part of the backup. 

I ran the restore. Rebooted. I have the same problem as before, opening Nautilus via Places/Home Folder OR Desktop or the rest opens not Nautilus but puts Rhythmbox on the upper panel.

All applications have no upper border with the three icons:
"x" for close
the "-" for make smaller
"box with wide top" for changing the window size from absolute to flexible.

At first I thought the problem was with compiz. For at every boot, I had to open System/Preferences/Appearance/Visual Effects and select "Normal". The system would open a "searching for drivers" and install them. Then I received a "keep settings" within 30 seconds or so "window". After the "Normal" was installed, the GUI apps worked without problem. But Places still opened Rhythmbox in the panel, i.e., no file manager.

I've posted about the foregoing and received some and no help. I cannot resolve the compiz business, although some posters responded. As for Nautilus versus Rhythmbox, I received no answers.

I'm at a loss as to know what to ask about. I would like to delete ALL my config files in /home/mark/*.config*. Is this a good idea? Is it going to damage my documents, data, stuff I saved. I don't mind another install. I just want to know what I'm doing, before I do it.

---

### Post by bruno9779 on 2009-12-12
Try with Gconf:

```
gconf-tool --set "/desktop/gnome/applications/component_viewer/exec" --type string "nautilus %s"
```

solution found [here]("http://ubuntuforums.org/showthread.php?t=1152101") googling "restore nautilus as default file browser"

Cheers!

---

### Post by Mark_in_Hollywood on 2009-12-12
HUH?

mark@Lexington-karmic-19:~$ gconf-tool --set "/desktop/gnome/applications/component_viewer/exec" --type string "nautilus %s"
No command 'gconf-tool' found, did you mean:
 Command 'gconftool' from package 'gconf2' (main)
gconf-tool: command not found

Does this mean that Karmic doesn't use gconf-tool? Any other ideas?

---

### Post by bruno9779 on 2009-12-12
try without the dash

---

### Post by Mark_in_Hollywood on 2009-12-12
I removed the - from gconftool. Ran the code. Terminal returned nada. Pulling down Places/Home Folder opened Rhythmbox in upper panel.

---

### Post by phillw on 2009-12-12
> **Mark_in_Hollywood said:**
> HUH?

mark@Lexington-karmic-19:~$ gconf-tool --set "/desktop/gnome/applications/component_viewer/exec" --type string "nautilus %s"
No command 'gconf-tool' found, did you mean:
 Command 'gconftool' from package 'gconf2' (main)
gconf-tool: command not found

Does this mean that Karmic doesn't use gconf-tool? Any other ideas?

If your ~home is backed up on a different drive, then you can mount it in any Ubuntu.

Once you have ANY version of Ubuntu running (live CD is okay), plug in your external device. It should either mount, or appear in places for you to mount.

hope that sorts it for you.

/edit following on from the psychocats tutorial - the making of an /old directory and mounting your /home area from the external drive should be a walk in the park.
If you want to see it on the desktop, then you'll want to mkdir /media/old and mount it there - once there - you can navigate it from your desktop

Hope that clears it up for you.,
Phill.

---

### Post by Mark_in_Hollywood on 2009-12-12
> **phillw said:**
> If your ~home is backed up on a different drive, then you can mount it in any Ubuntu.

Once you have ANY version of Ubuntu running (live CD is okay), plug in your external device. It should either mount, or appear in places for you to mount.

hope that sorts it for you.

/edit following on from the psychocats tutorial - the making of an /old directory and mounting your /home area from the external drive should be a walk in the park.
If you want to see it on the desktop, then you'll want to mkdir /media/old and mount it there - once there - you can navigate it from your desktop

Hope that clears it up for you.,
Phill.

None of this is relevant, whatsoever. Thanks.

---

### Post by phillw on 2009-12-12
> I use a separate /home via Psychocats.>  Upon the death of a relative this week, I had to restore the /home as legal docs were part of the backup. > /edit following on from the psychocats tutorial - the making of an /old directory and mounting your /home area from the external drive should be a walk in the park.
If you want to see it on the desktop, then you'll want to mkdir /media/old and mount it there - once there - you can navigate it from your desktop
I dunno -- mebbie I read it wrong - I thought it was relevent

Phill.
P.S. -- their method of transferring /home over is not really the best way. using rsync is better, as it is designed for that.
but, as it's irrelevent - I'll leave you to it. - Hope you get it sorted

---

