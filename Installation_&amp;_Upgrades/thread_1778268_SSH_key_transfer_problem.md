---
title: "SSH key transfer problem"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by kjuergen on 2011-06-08
Recently migrated to Xubuntu 11.04 and everything is now working as I hoped for except SSH.
I have the original id_rsa file which was generated on my old CentOS 5.x machine and copied it into my home directory (into .ssh). Somehow it looks like it can't find the key when I try to SSH into my remote server using exactly the same inputs. Do I somehow have to register the old SSH keys with the SSH which was installed by default??
I checked the properties of directory and file and I have full access to them.

Thanks,

Juergen

Problem was not SSH but Gnome Commander which didn't pass through the acceptance of the remote credentials. After running
ssh -p <port> <user>@<host> 
and accepting them it was stored in known hosts and Gnome commander could handle it..........

---

