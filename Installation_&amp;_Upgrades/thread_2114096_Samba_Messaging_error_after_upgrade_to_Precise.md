---
title: "Samba Messaging error after upgrade to Precise"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by Carl Foxmarten on 2013-02-09
I'd been running XUbuntu Maverick for quite a while after it was discontinued because it actually worked and didn't have problems with GTK2 applications mixed with GTK3 applications and the theming issues caused by not having one or the other.

Today I upgraded that computer all the way up to Precise, and have run into a problem with Samba that I haven't figured out how to fix just yet.

Because I run two computers, it's often helpful to send URLs and other text between them so I can post stuff without having to manually type it out.

The problem is that the command I used to use to send messages between computers (originally aided by LinPopup, which is now discontinued) doesn't work any more:

```
$ smbclient -N -M shale
Connection to //shale failed. Error NT_STATUS_BAD_NETWORK_NAME
```

What I've found so far points to not having the 'tmp' service set up properly, but that doesn't seem to be the case here.

Anybody have any suggestions? And should I post my 'smb.conf' file here?

---

