---
title: "Authentication error upgrading to 10.10 from 10.04"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by Mila on 2011-03-20
I'm trying to upgrade my 10.04 install to 10.10, using the "Upgrade" button on the Update Manager.

After clicking through the release notes, the upgrade release tool downloads, and then a popup appears: 

**Authentication failed**
Authenticating the upgrade failed. There may be a problem with the network or with the server. 

A quick googling indicates this might be a problem with gpg personal keys, and suggests running the *gpg* command with no arguments, which leads to an error:

gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC

Additional googling suggests upgrading libreadline6, but a sudo apt-get install libreadline6 indicates that libreadline6 is already installed and upgraded to the latest version.

We left the realm of me knowing what in the world is going on a while back -- so any help would be appreciated. :D

Thanks.

PS: My computer is an Acer Aspire 3810TZ. I have to do this sort of an upgrade because I have no CD drive and my BIOS has randomly decided to stop booting from USBs apparently.

---

### Post by sikander3786 on 2011-03-21
Either click the 'Check' button in Update Manager or go to Applications > Accessories > Terminal and refresh your repository index following this command.

```
sudo apt-get update
```

Hopefully, there shouldn't be any errors when you re-try upgrades. If the error persists, go to Software Center > Edit > Software Sources and choose 'Main' server for your downloads and click the 'Reload' button in the pop up window.

---

### Post by Dutch70 on 2011-03-21
Also, you may find this thread very useful. 
[[COLOR="Blue"]http://www.unix.com/ubuntu/123074-cant-update-use-package-manager-gpg-error.html[/COLOR]]("http://www.unix.com/ubuntu/123074-cant-update-use-package-manager-gpg-error.html")

---

### Post by Mila on 2011-03-21
I consistently get these errors when either clicking the "check" button in the update manager or running sudo apt-get update from the command line:

```
W: GPG error: http://archive.canonical.com lucid Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net lucid Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid-updates Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid-security Release: Unknown error executing gpgv
```

I have tried every solution on the forums and otherwise found by google for this. I actually used to get a lot more errors, but this is what I'm left with.

Working on a hunch (one of those hunches where you can't quite explain how you actually came to this conclusion), I downloaded the source code for the C++ readline library v. 6.0, recompiled, and replaced the old libreadline install with my new files. That got me down to a single error:

```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
```

... which I then fixed using the solution posted in the threads pertaining to what to do for a missing PUBKEY.

That seemed to do the trick, and now I can upgrade. Thanks for your help.

(Of course, this makes me wonder -- how many of those persistent gpgv errors popping up maybe have something to do with a bad readline library?)

Thanks!

Mila

---

### Post by Dutch70 on 2011-03-21
Isn't that just about the same thing they were talking about in post #7 of the link I gave you? 
> 
The problem wasn't gpg after all, but libreadline6. Updating it didn't help, but building it manually (md5: a3a5bf025a1b8df869f45f34098ffc6a rather than 2569b5ed629a3e573b0a8f9ec23a37ff) and copying my version to /usr/local/lib/libreadline.so.6 worked!

And then talked more about it in #16 & 17.

---

### Post by Mila on 2011-03-21
Yes. That was how I figured out that it was a gpg problem before coming to this forum at all. :D

I had originally tried their version of reinstalling and replacing the libreadline.so.6 file with the recompiled version, but that didn't work (same error.) I ended up uninstalling libreadline entirely, reinstalling, deleting the new files and replacing them with my own versions.

---

### Post by Dutch70 on 2011-03-21
Ahh, I see...lol. :)

Glad you got it worked out anyway. I was a little concerned how you were going to do that without being able to use a cd or usb.

---

