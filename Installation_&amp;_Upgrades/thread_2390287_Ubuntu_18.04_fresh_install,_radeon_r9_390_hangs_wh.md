---
title: "Ubuntu 18.04 fresh install, radeon r9 390 hangs when entering graphical"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by lilleman2 on 2018-04-27
Today I installed Ubuntu 18.04 via USB stick. A fresh install, cleaned out the whole disk.

To be able to get to the installer I had to pass "nomodeset" in the startup menu when booting from USB.

The system installed without problem, but when I removed the USB and booted the system, it only shows the loading screen and then (when entering GDM?) it freezes/crashes.

When investigating the filesystem, I found the related errors, I think, in /var/log/syslog : 

```
Apr 27 18:54:36 rex nm-dispatcher: req:1 'connectivity-change': new request (1 scripts)
Apr 27 18:54:36 rex nm-dispatcher: req:1 'connectivity-change': start running ordered scripts...
Apr 27 18:54:37 rex kernel: [   22.875988] radeon 0000:01:00.0: ring 4 stalled for more than 10240msec
Apr 27 18:54:37 rex kernel: [   22.875995] radeon 0000:01:00.0: GPU lockup (current fence id 0x000000000000002e last fence id 0x000000000000002f on ring 4)
Apr 27 18:54:37 rex whoopsie[1636]: [18:54:37] online
Apr 27 18:54:38 rex kernel: [   23.387987] radeon 0000:01:00.0: ring 4 stalled for more than 10752msec
Apr 27 18:54:38 rex kernel: [   23.387993] radeon 0000:01:00.0: GPU lockup (current fence id 0x000000000000002e last fence id 0x000000000000002f on ring 4)
Apr 27 18:54:38 rex kernel: [   23.899988] radeon 0000:01:00.0: ring 4 stalled for more than 11264msec
Apr 27 18:54:38 rex kernel: [   23.899994] radeon 0000:01:00.0: GPU lockup (current fence id 0x000000000000002e last fence id 0x000000000000002f on ring 4)
```

Then a lot more lines like them, and after that:

```
Apr 27 18:54:52 rex kernel: [   37.211993] radeon 0000:01:00.0: GPU lockup (current fence id 0x000000000000002e last fence id 0x000000000000002f on ring 4)
Apr 27 18:54:52 rex gsd-color[1740]: failed to refresh: Timeout was reached
Apr 27 18:54:52 rex kernel: [   37.723987] radeon 0000:01:00.0: ring 4 stalled for more than 25088msec
Apr 27 18:54:52 rex kernel: [   37.723993] radeon 0000:01:00.0: GPU lockup (current fence id 0x000000000000002e last fence id 0x000000000000002f on ring 4)
Apr 27 18:54:53 rex kernel: [   38.235987] radeon 0000:01:00.0: ring 4 stalled for more than 25600msec
Apr 27 18:54:53 rex kernel: [   38.235993] radeon 0000:01:00.0: GPU lockup (current fence id 0x000000000000002e last fence id 0x000000000000002f on ring 4)
Apr 27 18:54:53 rex kernel: [   38.747989] radeon 0000:01:00.0: ring 4 stalled for more than 26112msec
Apr 27 18:54:53 rex kernel: [   38.747995] radeon 0000:01:00.0: GPU lockup (current fence id 0x000000000000002e last fence id 0x000000000000002f on ring 4)
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^
```

Yes, the ^@:s is a part of that. There are lot more of them, but I did not want to spam.

Right now I am stuck, I do not know how to enter my new installation and I do not know how to fix this issue.

I remember it being hell getting my radeon r9 390 to work on my 4k screen with Ubuntu 16.04 and I have to send some extra commands to some driver file to make some flickering go away, but at least it works. :)

---

### Post by QIII on 2018-04-27
Hello!

Please use code tags around all terminal commands and their output.  This maintains formatting and makes your post easier to read.  It also keeps your post from appearing overly "spammy".

To use code tags, either:

1.  Click the # button in the tool bars above the text input box, place your cursor between the code tags that appear and type or paste your text.

2.  Type or paste your text, highlight it and then click the # button.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

Was there more text after the @ symbols?  If you paste it all between code tags, we can take a look at it.  There might be something important at the end.

Thanks.

---

### Post by lilleman2 on 2018-05-07
Thanks for the edit and tips. I'll make sure to make use of the code snippets in the future. :)

Sadly there were no more symbols after the @:s

However there were a LOT of them, spanning multiple pages in the console.

---

### Post by chuchofett on 2018-11-08
where you able to resolve this issue??

I'm trying to install ubuntu 18.04 myself and found with many similarities...

-I have dual 4k monitors
-I'm using radeon r9 390

I get my setup/desktop (whether I select try or install) hanged after a few seconds.. then mouse, then display goes out .. and not even hitting my power button does anything.. it's completely non-responsive... I'm trying a second USB Drive and if not i'm trying the "nomodset" command line, but I'm worried after I complete installation I won't get a working OS.. thanks and sorry for the old bump .. I couldn't found a newer complaint about this.

---

