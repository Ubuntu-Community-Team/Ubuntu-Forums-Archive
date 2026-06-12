---
title: "Netbook Remix?"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by spotdog14 on 2009-10-01
I have a problem with the 9.10 Netbook Remix. All of the .deb's I have downloaded off the net (Google Chrome, Drop Box, etc.) have not worked, they all give me the same error message:

"dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor."

Any ideas on what it could be? I am running it on a Dell Mini 9 and I downloaded the 32bit versions of the software... I am assuming that the Netbook Remix is not 64bit?

---

### Post by snowpine on 2009-10-01
Please post the output of the terminal command:

```
uname -a
```

This will tell you for sure which architecture you're using (32, 64, or lpia).

In general, it is a bad idea to randomly download things from the net... most of what you need can be found in the Ubuntu repositories... this is doubly true if you're using an unreleased development version like Karmic... since 9.10 is still in beta, most 3rd parties don't support it yet. ;)

---

### Post by peterthewolf on 2009-10-01
Why bother with the remix 
Koala 6 installs perfectly on my hp2133 netbook and is a fast as I can handle.:lolflag:

---

### Post by novafluxx on 2009-10-01
> **spotdog14 said:**
> I have a problem with the 9.10 Netbook Remix. All of the .deb's I have downloaded off the net (Google Chrome, Drop Box, etc.) have not worked, they all give me the same error message:

```
dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor.
```

Any ideas on what it could be? I am running it on a Dell Mini 9 and I downloaded the 32bit versions of the software... I am assuming that the Netbook Remix is not 64bit?

I get the same problem with Chrome

---

### Post by blakamin on 2009-10-01
That is because the debs will be telling the system they are for jaunty and not karmic...

use "sudo dpkg -i <name_of_deb_here>" in terminal

bug in [launchpad]("https://bugs.launchpad.net/ubuntu/+source/vte/+bug/388953")

It's a well-known bug [http://ubuntuforums.org/showthread.php?t=1273828]("http://ubuntuforums.org/showthread.php?t=1273828")
[URL="https://bugs.launchpad.net/ubuntu/+source/vte/+bug/438266"]
This is fixed, but its not accepted for beta so it will go in right after beta[/URL]

---

### Post by spotdog14 on 2009-10-01
> **snowpine said:**
> Please post the output of the terminal command:

```
uname -a
```

This will tell you for sure which architecture you're using (32, 64, or lpia).

In general, it is a bad idea to randomly download things from the net... most of what you need can be found in the Ubuntu repositories... this is doubly true if you're using an unreleased development version like Karmic... since 9.10 is still in beta, most 3rd parties don't support it yet. ;)


Linux Mini 2.6.31-11-generic #36-Ubuntu SMP Fri Sep 25 06:37:51 UTC 2009 i686 GNU/Linux

---

