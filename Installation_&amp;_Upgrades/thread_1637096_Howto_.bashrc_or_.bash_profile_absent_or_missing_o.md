---
title: "Howto: .bashrc or .bash_profile absent or missing on install"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by ToFue on 2010-12-04
As the title suggests.. though this is more of a guide for people experiencing the same thing I have - I'm just giving back ;)

 Normally I install newer distro releases cleanly, only deleting the sys-specific things in my home folder that can't be replaced with a new install (everything that's not Downloads, Documents, Videos, Music, or other user content that contains personal files I wish to keep, etc..) This also includes every hidden folder/file that I don't care to bring over, relying on the install & new system config to create what it needs..

 Conventionally, this install method also included deleting bash related files in my home directory, as the new install ought to have created a new profile.  This didn't happen with Maverick, though, as symptom-ed by the lack of color difference of file types when using 'ls' in terminal.. 

 My 'quick' cure was to take the following steps:

System>Users and Groups
  create a new frivolous user,

Applications>Accessories>Terminal

  ```


## copy the bash relevant from new account home dir to main user's home dir:

$ sudo cp /home/<new-user>/{.bashrc,.bash_logout,.profile} /home/${USER}/

## then change ownership:

$ sudo chown ${USER}: /home/${USER}/{.bashrc,.bash_logout,.profile}


```

permissions should remain intact.. 

Exit terminal, then open terminal again, then type 'ls' to verify the change.

now delete the frivolous user that was made, and all done :p

---

### Post by ToFue on 2012-09-25
:oops:> **ToFue said:**
>  Normally I install newer distro releases cleanly, only deleting the sys-specific things in my home folder that **can't be replaced** with a new install ...":oops:


I appologize for this gross oversight on my part, as it should have read : "Normally I install newer distro releases cleanly, only deleting the sys-specific things in my home folder that **can be replaced** with a new install ..."  

Bottom line in this method, you want to keep your irreplaceable and custom files, and lose the ones that a new system install will create..

I couldn't live with myself discovering that this was out there, unfixed!

---

