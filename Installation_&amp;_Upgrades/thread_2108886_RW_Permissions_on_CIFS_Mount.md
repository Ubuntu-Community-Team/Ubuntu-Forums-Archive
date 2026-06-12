---
title: "RW Permissions on CIFS Mount"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by Danny Rafferty on 2013-01-25
Hi everyone,
            Recently completed a new install of 12.04 on my netbook and I am trying to mount a Windows share for the purposes of backing up images and also accessing my existing media and document files on the Windows box.

I did have this working on 8.04 back in 2009/2010.

Essentially I can successfully mount and access the share, but cannot copy up files, or edit files - it's as if I am connected in a read-only mode or the Windows permissions aren't being read properly.

I have tried mounting with mount -t cifs and with mount.cifs.
I have tried using the rw option on both commands but this does not seem to make a difference.

Regards,

Danny.

---

### Post by SeijiSensei on 2013-01-25
Are you using a "[credentials]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")" file to log into the share with your Windows username and password?

If you are trying to mount with CIFS from the command prompt, see [this](http://serverfault.com/questions/367934/how-do-i-pass-credential-file-to-mount-cifs).

In Kubuntu you can mount a Windows share from the Dolphin file manager by entering the URL smb://user@server/share/ in the address box.  You'll be prompted for the password.  I believe Nautilus supports the same syntax.

---

