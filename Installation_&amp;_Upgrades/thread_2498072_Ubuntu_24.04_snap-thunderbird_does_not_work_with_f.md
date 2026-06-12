---
title: "Ubuntu 24.04: snap-thunderbird does not work with files on extenal partition! Fix?"
date: 2024-05-29
forum: Installation &amp; Upgrades
---

### Post by siggi2 on 2024-05-29
Hi,
I recently upgraded from Ubuntu 23.10 to 24.04. Everything works fine, except thunderbird. Befrore 24.04, thunderbird worked fine decades-long installed```

``` as default Ubuntu deb-package. Now it is a snap-thunderbird which, I was told, could not load my personal files that reside on an external ext4-partion on the same drive, because snap cannot do that:

Disk /dev/nvme0n1: 512GB

Number  Start   End     Size    File system     Name               
....
9      434GB   487GB   53.2GB  ext4            Ubu2404
10      487GB   496GB   8655MB  ext4            ext4Free
11      496GB   512GB   16.1GB  ext4            UbuTbird

Ubuntu 24.04 runs on partition 9 (Ubu2404), thunderbird gets my  profile data from partition 11 (UbuTbird), that is it got it, but not any more. Whenever I try to create my personal thunderbird profile anew with
```
$ thunderbird -p
```
I get error messages such as 
```
Profile couldn’t be created. Probably the chosen folder isn’t writable.
[Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIToolkitProfileService.createProfile]"  nsresult: "0x80520015 (NS_ERROR_FILE_ACCESS_DENIED)"  location: "JS frame :: chrome://mozapps/content/profile/createProfileWizard.js :: onFinish :: line 236"  data: no]
```

I was told that, contrary to the old deb-thunderbird, the new snap thunderbird in Ubuntu 24.04 cannot access data on an external partition outside of snap. 

_How can I, please, tell the snap thunderbird "do get my personal mail files from the external partition UbuTbird"?_

Thanks, siggi2

P.S. Currently I make do with deb thunderbird according to [https://ubuntuhandbook.org/index.php/2024/03/install-thunderbird-deb-ubuntu-2404]("https://ubuntuhandbook.org/index.php/2024/03/install-thunderbird-deb-ubuntu-2404"), but I dearly would prefer the default snp-thunderbird

---

### Post by philhughes on 2024-05-30
What does the output of the following show?

```
snap connections thunderbird
```

If it shows something like the following in the output:

```
...
removable-media         thunderbird:removable-media         -         -
```

then try this command:

```
snap connect thunderbird:removable-media
```

It should then show:

```
removable-media         thunderbird:removable-media         :removable-media         -
```

I don't have Thunderbird snap installed to try, but this may solve it.

---

### Post by siggi2 on 2024-05-30
> **philhughes said:**
> What does the output of the following show?

```
snap connections thunderbird
```

If it shows something like the following in the output:

```
...
removable-media         thunderbird:removable-media         -         -
```

Yes, it did!

> 
then try this command:

```
snap connect thunderbird:removable-media
```

It should then show:

```
removable-media         thunderbird:removable-media         :removable-media         -
```


Yes, after repeating "snap connections thunderbird", it performed  exactly like that!

However, after having created my thunderbird profile starting with
```
$ thunderbird -p
```
and start thunderbird, a small red message box with red text occurs, see attachment  Screenshot20240530165037.png. I close this message boxt and can read the error messages on my terminal window:
```
~$ thunderbird -p
Gtk-Message: 16:53:54.522: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.
[GFX1-]: glxtest: libpci missing
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
console.error: (new UnknownError("IndexedDB: thunderbird/url-classifier-skip-urls getLastModified() IndexedDB:   The operation failed for reasons unrelated to the database itself and not covered by any other error code.", "resource://services-settings/IDBHelpers.jsm", 18))
JavaScript error: resource://gre/modules/AsyncShutdown.sys.mjs, line 724: Error: Phase "xpcom-will-shutdown" is finished, it is too late to register completion condition "UserInteractionTimer 1 for document 741c9b5b9e00"
Gtk-Message: 16:54:18.647: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.
[ImapModuleLoader] Using nsImapService.cpp
[GFX1-]: glxtest: libpci missing
console.error: (new TypeError("window.gTabmail is undefined", "chrome://messenger/content/parent/ext-mail.js", 766))
~$
```

It seems to be general problem outside of thunderbird? Somewhere I read snap cannot access external partitions and one has to bind them somehow so that snap can access them?

Might this be the problem here?

**EDIT: ** The above code line
```
removable-media         thunderbird:removable-media         :removable-media         -
```
"Yes, after repeating "snap connections thunderbird", it performed  exactly like that!"

should read for completeness:
```
removable-media         thunderbird:removable-media           :removable-media                manual
```

"manual" at the end of the line was missing

---

### Post by philhughes on 2024-05-30
Sorry about the missing "manual".

The "snap connect" command is what allows the snap to access external partitions.

When I run "thunderbird -p" on my Ubuntu 23.10 .deb installation, I also see these errors:

```
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
console.error: (new UnknownError("IndexedDB: thunderbird/url-classifier-skip-urls getLastModified() IndexedDB:   The operation failed for reasons unrelated to the database itself and not covered by any other error code.", "resource://services-settings/IDBHelpers.jsm", 18))
```

so I don't think these are the source of the problem. It appears that you have a missing library (libpci).

After starting Thunderbird with -p , you should see the window in the attached screenshot.

If you are feeling brave, you could try installing this if it is not already installed:

```
sudo apt install libpci3
```

This link provides a bit of information on Firefox, which shares code with Thunderbird:

[https://github.com/mozilla/geckodriver/issues/1877](https://github.com/mozilla/geckodriver/issues/1877)

Otherwise, I'd report a bug.

Edit: forgot to attach screenshot.

---

### Post by siggi2 on 2024-05-30
Thank you **philhughes** for your efforts :-)
> ...It appears that you have a missing library (libpci)...
No I did not. And after I had lost my thunderbird profile files for three accounts while trying to "bind" to within snap(luckily could recover a slightly older version fo my personal folder) and after a lot of turmoil with "snapping" I quit and returned to deb-thunderbird.   
Thank you again anyway,
siggi

---

### Post by evereasy on 2024-06-02
siggi2, thank you for reporting this issue. That helps me a lot, becuase I had the exactly same issue. Here is the workaround that I use after I found the following thread mentioned about /mnt.
[how do I ensure that I install a NON-Snap version of an application (Thunderbird)]("https://ubuntuforums.org/showthread.php?t=2434651")

1. Run the command suggested by philhughes 
```
[COLOR=#000000][FONT=&amp]snap connect thunderbird:removable-media[/FONT][/COLOR]
```

2. Mount my Thunderbird profile directory under /mnt

Hope this can solve your issue too.

---

### Post by siggi2 on 2024-06-02
Thank you even more, **evereasy**!

Your solution seems to work great :)  A few comments and questions will follow some time later.

Take care, siggi

---

### Post by siggi2 on 2024-06-02
This 
"$ snap connect thunderbird:removable-media"
will I have to input it after each update or upgrade?
Otherwise there is not much to say, I am just happy :-D

---

### Post by deadflowr on 2024-06-02
Once any connection is set it's set forever.

---

### Post by siggi2 on 2024-06-03
Thank you, **deadflowr**!

---

### Post by philhughes on 2024-06-05
For reference, on a 23.10 system updated to 24.04 (with Thunderbird snap), I see the glxtest error when running "thunderbird -p", so I don't think this was relevant to your problems. The profile dialogue box correctly appears.

```
$ thunderbird -p
Gtk-Message: 11:22:03.241: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.
[GFX1-]: glxtest: libpci missing
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
JavaScript error: resource://gre/modules/XULStore.sys.mjs, line 60: Error: Can't find profile directory.
```

---

### Post by siggi2 on 2024-06-06
Thank you for mentioning it, but I had error messages by using 
```
"thunderbird -p"
``` 
even long before 23.10, so they bothered me in no way because everything had been going smoothly afterwards.

---

### Post by jfberar on 2024-06-10
If /home is on another partition, snap will not allow access through symlink or bind mount . You have to reconfigure it according  *doc.ubuntu-fr.org/snap* using :

snap refresh --channel=latest/edge snapd
snap set system homedirs=/MountedPartition/home

and modify in /etc/passwd  the userline    /home/$USER => /MountedPartition/home/$USER

Then thunderbird will ccess to /MountedPartition/home/$USER/.thunderbird

But the problem still exists if you have users in various partitions

jfrancois

---

