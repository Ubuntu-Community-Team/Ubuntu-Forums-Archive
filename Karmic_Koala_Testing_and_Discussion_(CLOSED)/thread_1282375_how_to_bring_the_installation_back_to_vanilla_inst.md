---
title: "how to bring the installation back to vanilla install.."
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rednus on 2009-10-04
gurus.. quick question.. i have installed lot of packages and software.. and removed a lot since i install my first alpha.. how do i get it back to vanilla install of beta without loosing my user data and settings?

thanks in advance

---

### Post by slakkie on 2009-10-04
Well, not easy. You need some kind of record what you had installed. If you had done dpkg --get-selections > package.list before removing packages, you could have restored them afterwards by doing:

```

# Backup package list
dpkg --get-selections > package.list
# Restore
sudo dpkg --set-selections < package.list
sudo apt-get dselect-upgrade

```

If you have not purged packages, you could be in luck:

```

pkgs=$(dpkg -l | tail -n +6  | grep -v "^ii" | awk '{print $2}')
[ -n "$pkgs" ] && sudo aptitude install $pkgs

```

---

### Post by psyke83 on 2009-10-04
You could boot from the desktop CD and take the --get-selections output from there. After all, that is a vanilla installation.

---

### Post by aamukahvi on 2009-10-04
Also, if your /home is on a different partition, you could just reinstall and not format /home. Backups recommended.

---

