---
title: "Repairing ubuntu (permissions?) from Live CD after failed updates"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by rootSU on 2011-09-24
Hi there, I need some urgent help please

My 11.04 installation broke during routine updates using update manager.

On boot I get an error "could not update ICE authority" and when the  standard desktop loads, it looks more like the 10.04 one.  I get another  error saying that /home/dan/.config permissions denied so it cannot  load my desktop properly.

When I launch Terminal I get an error about permissions being denied to .bashrc

If I CTRL, ALT +F2 I get to TTY and it all operates as normal.

I tried:
     Code:
     sudo chmod 644 /home/dan/.dmrc sudo chmod 755 /home/dan sudo chown dan: /home/dan sudo shutdown -r now 
Which seemed to go without a hitch but my issue still remains.

I can boot to the live CD and access all the directories including /home, /usr etc.

Does anyone know how I can fix this from here?
I want to keep my data, thats a given, but I really would like to keep  all my packages too.  It really does seem like a broken permissions  issue, but I am still ubuntu / linux noob.

I am a wintel systems engineer though so I am happy to try complex  solutions to repair this but as I still don't understand all the  commands, I will need some guidance.

My last resort is to reinstall ubuntu from live CD without formatting  home and keeping the same username, but that will lose all my android  building set up etc etc.

Any suggestions gratefully appreciated...

---

### Post by dino99 on 2011-09-24
is it a standard installation ?

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

you should be able to fix the package(s) upgrading by booting into recovery mode:

hold "shift" key down at bios end process to get the grub menu, select the 2d line (recovery mode), then select "repair packages"

---

### Post by rootSU on 2011-09-24
> **dino99 said:**
> is it a standard installation ?

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

you should be able to fix the package(s) upgrading by booting into recovery mode:

hold "shift" key down at bios end process to get the grub menu, select the 2d line (recovery mode), then select "repair packages"

Hi,

Thank you for the suggestion.  It is a standard installation of 11.04.

I tried repairing broken packages.  It went through very quickly.  It prompted as it would with apt -get but I still have the issue.

After:
```
"could not update ICEauthority"
```I get:
```
"There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"
```Then when the desktop starts up, its actually permission denied to /home/dan/.config/monitors.xml, which makes sense.

edit> Not sure if this is relevant but before "restart to complete updates", but I had removed gtk RGBA due to a compatability issue I was having with VMware player.

The system also hung at shutdown when "restart" was chosen.  I do get some hangs at restart anyway, perhaps to do with my NTFS NAS, although this was for the mostpart, addressed.  I FOOLISHLY decided to force shutdown

---

### Post by ajgreeny on 2011-09-24
maybe you can boot to recovery mode then run ```
chown -R username:username /home/username
``` and also ```
chmod -R 755 /home/username
``` That will at least mean that all your home is owned by you and has the theoretically correct permissions.  I'm not sure if it will solve this ICEauthority problem, but it is worth a try.

If still no go try ```
mv ~/.ICEauthority ~/.ICEauthority.old
``` and then try to login again.

---

### Post by rootSU on 2011-09-24
> **ajgreeny said:**
> maybe you can boot to recovery mode then run ```
chown -R username:username /home/username
``` and also ```
chmod -R 755 /home/username
``` That will at least mean that all your home is owned by you and has the theoretically correct permissions.  I'm not sure if it will solve this ICEauthority problem, but it is worth a try.

If still no go try ```
mv ~/.ICEauthority ~/.ICEauthority.old
``` and then try to login again.

Thank you for the suggestion.

I booted into recovery mode, dropped to root shell.

I ran:
```
chown -R dan:dan /home/dan
```With no errors.  It took quiet a while which was a good sign.

Then:
```
chmod -R 755 /home/dan
```Again, with no errors.

I restarted at this point.  Logged in and the 3 errors persisted.  The first 2, ok we possibly expected that. but I was concerned to still see permission denied on /home/dan/.config/monitors.xml

Restarted recovery mode and:
```
mv home/dan/.ICEauthority home/dan/.ICEauthority.old
```And it appeared to go through, but upon restart, all 3 errors persisted.

Booted into live CD and I can see that home/dan/.ICEauthority.old does indeed exist.  However, should a new .ICEauthority have been generated?  It hasn't.

So now all the permissions should be correct, but the permissions errors still persist.

Am I fighting a losing battle?

If I try to open places (which I am not sure why I have this on 11.04) I get an error stating that the file is not associated.  This is also happening with removable media.

It's quite frustrating as I can browse all the directories from the Live CD on the mounted HDD with no issue.  Unfortunately my Home Directory is 46GB just over, so backing that up to an NTFS NAS over wireless is going to be painstaking, especially since its write speed is quite low.

EDIT> FYI I can see a permissions change via Live CD now.  Instead of the files showing as "root", they show as "1000 -user #1000" which is my installation's UID for "dan"

Home itself still shows as "root"

---

### Post by rootSU on 2011-09-24
Partially resolved.

I installed Unity 2D and managed to log on.  I noticed my desktop was almost complete (allbeit in a unity 2d fashion minus my compiz settings).

I also noticed my file manager shortcut was missing and couldn't find nautilus.  I installed nautilus and now I can access all my programmes and directories.

Thanks for your input guys, this one was really bugging me.

Just doing a unity --replace currently/  Fingers corssed.  if that doesn't work thats another thread somewhere else.

---

