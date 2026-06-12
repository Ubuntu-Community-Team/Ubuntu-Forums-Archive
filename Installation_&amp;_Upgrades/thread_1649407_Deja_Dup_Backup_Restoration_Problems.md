---
title: "Deja Dup Backup Restoration Problems"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by amtur_poet on 2010-12-20
Last night, I used the Deja Dup backup program to backup all my data from my Wubi installation, and move it to a native Ubuntu installation. I backed all of the data in my home folder to a 32GB USB stick, and there were no problems during the backup process. However, now, when I am trying to restore the backup, it find the files, but when going into the "Restoring..." phase, there is no movement on the progress bar, and not text in the "Details" box. The access LED on my USB drive is also not illuminated. Any ideas on what I can do? It's a really sucky feeling knowing that you can't access your backup. :(

EDIT: I ran the program after restarting my computer, and got this error:
> Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1257, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1250, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1142, in main
    globals.gpg_profile.passphrase = get_passphrase(1, action)
  File "/usr/bin/duplicity", line 129, in get_passphrase
    pass1 = getpass.getpass("GnuPG passphrase: ")
  File "/usr/lib/python2.6/getpass.py", line 83, in unix_getpass
    passwd = fallback_getpass(prompt, stream)
  File "/usr/lib/python2.6/getpass.py", line 118, in fallback_getpass
    return _raw_input(prompt, stream)
  File "/usr/lib/python2.6/getpass.py", line 135, in _raw_input
    raise EOFError
EOFError

---

### Post by mikix on 2010-12-22
Hello!  You are being affected by [https://bugs.launchpad.net/deja-dup/+bug/582720](https://bugs.launchpad.net/deja-dup/+bug/582720)

To grab the fixed package, follow the instructions here: [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

If this works for you, I would really appreciate you leaving a comment in that bug verifying that the fix worked, so that this update can go out to everyone.

---

