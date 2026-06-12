---
title: "ecryptfs keys no longer in keyring after unmounting private directory"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by johannr on 2011-05-15
The upgrade from Maverick -> Natty seems to have broken the way ecryptfs works with my system using SSH and passwordless logins (Pubkey auth). On maverick, once the key was in the keyring, it stayed put even after the encrypted filesystem had been unmounted. When I then logged onto my remote system with ssh and pubkey auth, the ecryptfs was automatically mounted as the key was still in the keyring. This is important as I need access to the encrypted directories in non-interactive automated  passwordless ssh in cron scripts. So I just had to load the key once after reboot by logging in with my password, and then I could use ssh pubkey auth from then on, and the ecryptfs Private directory would nevertheless be mounted automatically on login.

With natty this has changed. I suppose it may have to do with this:
[http://www.ubuntuupdates.org/packages/show/261140](http://www.ubuntuupdates.org/packages/show/261140)
Quoting from the page: 
" must insert keys during testing phase, since we remove keys on 
      unmount now, LP: #725862"

I can also confirm in an interactive session:
[jr@spin ~]$ keyctl list @u
keyring is empty
[jr@spin ~]$ ecryptfs-mount-private 
Enter your login passphrase:
Inserted auth tok with sig [5175883cfc951370] into the user session keyring
[jr@spin ~]$ keyctl list @u
2 keys in keyring:
1060371348: --alswrv  1001  1001 user: 19b2ef0fbd7fe7fa
1038603617: --alswrv  1001  1001 user: 5175883cfc951370
[jr@spin ~]$ ecryptfs-umount-private 
[jr@spin ~]$ keyctl list @u
keyring is empty

So my questions:
1. Is this indeed intended behavior?
2. Is there a way to "fix" /work around this, so that the keys are kept in the keyring to re-enable the behavior like on maverick?

This really breaks my scripts....
Thanks
--johannr

---

