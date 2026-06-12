---
title: "Focus and mouse Redirection problem"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by JoelParke on 2012-11-12
I recently upgraded to 12.10 and now about every 4th or 5th time I click on one of the buttons in eclipse, I am redirected seemingly randomly to one of the apps on the lanchpad.  This horrible.  

As an attempted work around I have used the  gnome-tweak-tool to set the Windows Focus Mode to 'Mouse' BUT this doesn't help.  Has anyone else seen this problem?? Do I have a broken version of Unity?  What gives?  

Any help would be GREATLY appreciated.  I would hate to have to revert to 12.04.

THANKS!  :mad:

---

### Post by JoelParke on 2012-11-13
I have determined that this issue was caused by the two displays that I use.  I switched to a single display and the problem vanished.  

After using this single display for a while and then logging out and then back in, and then turning on both displays, the problem seems to have disappeared.  I will report back if this issue reappears. 

I hope this helps someone else with this problem.

---

### Post by JoelParke on 2012-11-17
I am continuing to struggle with this problem.  Again and again I have horrible issues with the focus.  For example, I am in the middle of debugging in eclipse that then I will click on the inspect dialog and the WHAM, either something like LibreOffice will pop up, or perhaps eclipse will close or some other app that is not running will be invoked.  THIS IS HORRIBLE.  

Can anyone suggest something else to try?  Things are much better than they were at first when I switched to one monitor only and then logged out, then back in, and then switched back to two monitors.  But the issues still plagues me.  

I have never seen anything like this before.  I love Ubuntu, but I hate the thought of trying to go back to 12.04.  Is there anyway that the problems with unity could be causing this?  OR is there an easy way to reinstall without loosing all my customization?

Thanks for your help.

---

### Post by JoelParke on 2012-11-20
As I continue to struggle with this issue.  It seems clear that the BUG is in the process that determines which application should be passed a mouse click.  For several minutes everything works as it should.  THEN when I click on one application that seemingly has the focus, the click is sent to one of my applications in the Unity Launcher.  

It there an easy way to uninstall and then reinstall Unity.  Since this seems to be where my current issue lives?  ANY help would be greatly appreciated.

---

### Post by JoelParke on 2012-11-20
I have followed the answer here: [http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity](http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity) 
I will report back on the result -- to save others time.

---

### Post by JoelParke on 2012-11-20
My attempted remove of Unity -- did not help.  I suspect that I need a more complete removal of Unity.  Is that possible?

THANKS

---

### Post by JoelParke on 2012-11-21
The next thing I tried was to reset Unity completely to default.  This seems to have helped ever so slightly, but not the fix I was hoping it would be.  There is clearly a BUG somewhere in the way that focus is passed around.   

I will keep working on this, but If anyone can shed some light.  This would be greatly appreciated.

---

### Post by JoelParke on 2012-11-27
Well -- I GIVE UP -- this is so bad that I have switched to the GNOME desktop -- which I don't really like -- but UNITY with the random change of focus, no matter what settings I use, is USE LESS.  I love Ubuntu, but this release has been so bad that I will probably return to 12.04 from my backups.

---

### Post by JoelParke on 2012-12-08
I discovered the primary issue is that FIRST: 3D support is missing in VirtualBox for my hardware.  I have a ATI Radeon HD 5700 Series card with excellent 3D functionality.  So when this support arrives, I may shift back to 12.10.  

SECOND:-( -- my backup using Deja-dup FAILED.  So I needed recreate everything from the portion of the backup that I could salvage.  (Unknown error) -- SO I have shifted to Clonezilla and saving a backup of the Virtual Disk.  This is much much better and I would highly recommend this path to others.   
1. Just backup your disk.vdi  -- then if any problems, just restore, and release the old disk using Virtual Storage Manager, then remove the memory of this dis.  2.  Attach the restore disk to the VM and all is well. 

The good news is that I now have a rebuilt Ubuntu without all the dead wood from prior installs.   Until the 3D support is transparent for VirtualBox, there should be a HUGE notice and warning.

---

