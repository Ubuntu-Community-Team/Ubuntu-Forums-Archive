---
title: "Ubuntu install home directory not owned by root"
date: 2015-10-28
forum: Installation &amp; Upgrades
---

### Post by matthew115 on 2015-10-28
Howdy,

I am trying to install a custom Ubuntu install but am having a few issues.  The custom install has been created by me using the LiveCDCustomization instructions.  I basically installed ssh and modified the wallpaper for right now.  I went to install my custom installer, but after it finished installing I was unable to login.  After a little bit of debugging, I figured out it was a permissions error.  More precisely the user account I created on install, called administrator, had the XAuthority file owned by root instead.  This was an easy fix, just corrected the permissions and logged in and it worked.  However, it was happening on every user that tried to login to the machine as well.  So digging into the problem a bit more now I see that the root home directory is not owned by root, but instead is owned by administrator.  After I change /home back to being owned by root, everything seems to work correctly again.

Does anyone know why my custom Ubuntu installation would change the permissions of /home to be owned by the first user created instead of root?  Or why the /home/<user>/.XAuthorty file is owned by root by default?  

Thanks for the help.

Short version:
/home not owned by root after install, owned by initial user instead (doesn't happen on default Ubuntu install)
/home/<user>/.XAuthority owned by root when user first tries to login.  Have to chown to user for them to login

---

