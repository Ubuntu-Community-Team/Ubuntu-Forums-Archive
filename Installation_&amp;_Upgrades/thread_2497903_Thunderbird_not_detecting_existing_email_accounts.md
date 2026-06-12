---
title: "Thunderbird not detecting existing email accounts"
date: 2024-05-22
forum: Installation &amp; Upgrades
---

### Post by Onesimus on 2024-05-22
I have upgraded from Ubuntu 23.10 to 24.04 and most things work.

However, the thunderbird does not recognise my existing email accounts.  

I have looked in: 
    snap/thunderbird/common/.thunderbird and my profile is in that folder.

When I start up thunderbird it wants me to start up a new account, and doesn't see any of my existing accounts.

Any ideas ?

---

### Post by currentshaft on 2024-05-22
Try running "thunderbird --profilemanager" in Terminal and see if it offers the option to use your existing profile.

---

### Post by Onesimus on 2024-05-23
No joy.  It did provide option to use existing profile and here's what I got

```
joe@onesimus:~$ thunderbird --profilemanager
Gtk-Message: 07:10:24.077: Failed to load module "xapp-gtk3-module"
Gtk-Message: 07:10:24.078: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.

(thunderbird:310177): Gtk-WARNING **: 07:10:24.172: GTK+ module /snap/thunderbird/470/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.
Gtk-Message: 07:10:24.172: Failed to load module "canberra-gtk-module"

(thunderbird:310177): Gtk-WARNING **: 07:10:24.175: GTK+ module /snap/thunderbird/470/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.
Gtk-Message: 07:10:24.176: Failed to load module "canberra-gtk-module"
[GFX1-]: glxtest: libpci missing
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
console.error: (new UnknownError("IndexedDB: thunderbird/url-classifier-skip-urls getLastModified() IndexedDB:   The operation failed for reasons unrelated to the database itself and not covered by any other error code.", "resource://services-settings/IDBHelpers.jsm", 18))
JavaScript error: resource://gre/modules/AsyncShutdown.sys.mjs, line 724: Error: Phase "xpcom-will-shutdown" is finished, it is too late to register completion condition "UserInteractionTimer 1 for document 74bdfc4bca00"
Gtk-Message: 07:10:34.951: Failed to load module "xapp-gtk3-module"
Gtk-Message: 07:10:34.952: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.

(thunderbird:310177): Gtk-WARNING **: 07:10:35.033: GTK+ module /snap/thunderbird/470/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.
Gtk-Message: 07:10:35.033: Failed to load module "canberra-gtk-module"

(thunderbird:310177): Gtk-WARNING **: 07:10:35.040: GTK+ module /snap/thunderbird/470/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.
Gtk-Message: 07:10:35.040: Failed to load module "canberra-gtk-module"
[ImapModuleLoader] Using nsImapService.cpp
[GFX1-]: glxtest: libpci missing
console.debug: "Found 0 public keys and 0 secret keys (0 protected, 0 unprotected)"
JavaScript error: chrome://messenger/content/aboutMessage.js, line 119: NS_ERROR_ILLEGAL_VALUE: Component returned failure code: 0x80070057 (NS_ERROR_ILLEGAL_VALUE) [nsIWebProgress.addProgressListener]
JavaScript error: chrome://messenger/content/preferences/general.js, line 2071: NS_ERROR_ILLEGAL_VALUE: Component returned failure code: 0x80070057 (NS_ERROR_ILLEGAL_VALUE) [nsIObserverService.removeObserver]

```

---

### Post by ajgreeny on 2024-05-23
This could be a result of the move from thunderbird being installed as a .deb from the repos to a snap version.
I have no idea if the snap automaticallypicks up the existing profiles that are in the hidden ~/.thunderbird folder in your home but check to see if that folder is present or not.

You could try downloading the .tar.bz archive direct from the thunderbird website, extracting it and then running thunderbird from the executable file it contains; this is how I now run thunderbird having removed the snap and never opened it.

Sorry I can't give you more info as I've not sen the snap version running and I don't know where the profile is stored for it buti suspect it may be in a separate folder in your home called **snap**.

The hidden .thunderbird  folder should still be in your home as far as I'm aware so search for it there and let us know so we can try to help you get back to "normal".

PS:
I have removed all snaps and the whole infrastructure from my now old hardware so my knowledge of them is very limited so other users may be more helpful if you decide to keep the snaps as your default versions.

---

### Post by Onesimus on 2024-05-23
Thanks for your reply ajgreeny.

I have a folder ~/.thunderbird which is left over from the .deb installation.
I also have ~/snap/thunderbird/common/.thunderbird

I moved the ~/snap/thunderbird/common/.thunderbird to an alternative location (mainly if things went wrong, I could move it back and start over). 
```
mv ~/snap/thunderbird/common/.thunderbird ~/snap/thunderbird/common/.thunderbird-org

```

I then copied the Deb .thunderbird to snap location
```
cp -a ~/.thunderbird ~/snap/thunderbird/common
```

Started up Thunderbird, and everything seems to be fine.  However, not totally impressed that an upgrade that has been released should fail on such a basic issue.

---

### Post by ajgreeny on 2024-05-23
Yes, I agree!
Hence my removal of anything to do with snaps; my hardware is just too old at present and all snap applications take far too long to start.

---

### Post by karyk on 2024-05-24
Maybe it would be a good idea to run an "export" in Thunderbird's app prior to upgrading.  I do so periodically just because i have seven email accounts in my Thunderbird setup, and it's a PITA to reenter them all from scratch.

If you did need to "import" after an upgrade you'd need to clean up the old files.

---

### Post by tomdkat on 2024-05-24
Wow, this thread is my saving grace!  I upgraded to Ubuntu 24.04 a couple of days ago and am actually using the system for the first time today.  I was shocked to be prompted to create a new account, given the DECADES of email I have on the system.  I'll try the copy approach (I hope I have enough disk space :) ).

Thanks for starting this thread!

---

### Post by prcowley on 2024-05-25
This is pretty appalling.
This issue with the SNAP Thunderbird was identified when people tried to force an upgrade to 24.4  It was an identified issue and a major one. I took note as I too have decades of email stored in Thunderbird, fortunately all in IMAP format

When my Ubuntu 23.11 started indicating the 24.4 upgrade was now available I thought they would have fixed this showstopper. (I had previously tried an earlier version of a SNAP based Thunderbird but it was useless so since I had not deleted the .DEB version, thankfully, I just uninstalled the SNAP as thoroughly "under cooked" (and thus was an Ubuntu version)
I have been pretty wary, and red flags abounded!!, so didn't jump in immediately and started searching for any issues related to the new SNAP Thunderbird version and I am very glad I did. 

 I not against SNAPs in general, but the email client is a pretty sensitive component of our daily information interface and given the already identified issues from the 24.04 release date I feel it should have been fully sorted out before allowing 24.04 up gradable to be available.
I am going to wait a bit longer and see if there are any other issues. Being on IMAP lessons the risk of losing email but I will take the advice of backing up my .deb Thunderbird profile before I take the plunge. But it is a huge pain if I have to set up 8 different accounts separately again and then wait for all those old emails to download. I really don't want to put myself though that again.

Cheers
Pete Cowley

---

### Post by dragonfly41 on 2024-06-17
> [COLOR=#000000]I will take the advice of backing up my .deb [/COLOR][COLOR=#417394]Thunderbird[/COLOR][COLOR=#000000] profile before I take the plunge. But it is a huge pain if I have to set up 8 different accounts separately again and then wait for all those old emails to download. I really don't want to put myself though that again.
[/COLOR]Thanks for the heads up on Thunderbird. I arrived at this thread because one of several IMAP accounts has ceased to work and I'm browsing around picking up tips on how to troubleshoot. Not sure yet if it is due to mail service provider or Thunderbird. 
I will certainly avoid snap.
I will just add here that I have a Thunderbird extension installed ImportExport NG on Ubuntu 22.04.
[https://github.com/thundernest/import-export-tools-ng](https://github.com/thundernest/import-export-tools-ng)
This might help in migrating/backing up profile. I note that profile can be viewed in Evolution which I have now installed as backup client.

---

### Post by Dr. C on 2024-09-14
> **Onesimus said:**
> Thanks for your reply ajgreeny.

I have a folder ~/.thunderbird which is left over from the .deb installation.
I also have ~/snap/thunderbird/common/.thunderbird

I moved the ~/snap/thunderbird/common/.thunderbird to an alternative location (mainly if things went wrong, I could move it back and start over). 
```
mv ~/snap/thunderbird/common/.thunderbird ~/snap/thunderbird/common/.thunderbird-org

```

I then copied the Deb .thunderbird to snap location
```
cp -a ~/.thunderbird ~/snap/thunderbird/common
```

Started up Thunderbird, and everything seems to be fine.  However, not totally impressed that an upgrade that has been released should fail on such a basic issue.


The above worked for me. After backing up both the the old (.deb) ~/.thunderbird folder and the ~/snap/thunderbird/common/.thunderbird folder to a backup directory, I replaced the .thunderbird folder in the snap location with the old .thunderbird folder. Strangely enough I did not run into this issue when a friend of mine upgraded from 22.04 to 24.04. I must add that my Thunderbird folder is like 20 years old migrated initially from Windows XP to Ubuntu 6.06!

---

### Post by 1uhost on 2024-09-15
Worked for me! Thanks :o

---

