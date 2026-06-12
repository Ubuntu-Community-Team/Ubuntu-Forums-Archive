---
title: "querying package database"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by wishartz on 2006-10-13
Does anybody know how to query the package database, so you can find out wich packages are installed on your system?

I've been using ubuntu for about three months now  ( and loving it), coming from a redhat sort of background, where you used rpm -qa <packageame>  to query whether it was installed etc.  Can anybody tell me how I can do this with Ubuntu.  I've looked at the apt-get documentation and cannot find anything similar.

The reason for this post is, I updated my system the other day and it broke my compiz and I want to check that it isn't still installed and start from scratch by installing it again.

I used this command to remove it  

sudo aptitude remove compiz compiz-gnome

but want to make sure everything is removed.  

Any help would be greatly appreciated.  Thanks.

---

### Post by Kateikyoushi on 2006-10-13
You can use Synaptic for this.

System >> administration >> Synaptic package manager.

There you can list all the installad packages in your system or can run  search for a package and will see it's status.

If you prefer command line.

```
sudo aptitude search "packagename"
```

If the line starts with an "i" the package is installed.

---

### Post by wishartz on 2006-10-15
Thanks for the help.

---

