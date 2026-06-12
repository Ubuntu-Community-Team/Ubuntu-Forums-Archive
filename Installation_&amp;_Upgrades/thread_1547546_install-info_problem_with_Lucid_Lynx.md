---
title: "install-info problem with Lucid Lynx"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by maxleonca on 2010-08-06
Hi,
I just installed a fresh copy of Lucid Lynx and everything works like a charm.
But when I ran the update manager I started to have some problems.
1st was that the libc6 update lost dependencies and synaptic couldn't fixed them (or I didn't knew how), but I looked for the packages manually and download them and install them by hand and problem solved.

And now I'm getting an error from install-info:
```

Setting up install-info (4.13a.dfsg.1-5ubuntu1) ... 
/usr/sbin/update-info-dir: line 51 17894 Done                    find "$INFODIR" -type f
         17895 Segmentation fault     | while read file; do
         case $file in
                 */dir | */dir.gz | */dir.old | */dir.old.gz | *-[0-9] |*-[0-9].gz | *-[0-9][0-9] | *-[0-9][0-9].gz | *.png)
                 continue
         ;;
         *)
             ginstall-info "$file" "INFODIR/dir" || { errors=$[errors+1]; }
         ;;
esac;
done
dpkg: error processing install-info (--install_:
 subprocess installed post-installtion script returned error exit status 139
Processing triggers for man-db ...
Error where encountered whole processing:
 install-info

```When I type:
```

echo $INSTALLDIR

```I get nothing.

Any ideas will be more than welcome.

---

### Post by pastalavista on 2010-08-06
Try ```
sudo dpkg --configure -a
sudo apt-get install -f
and then (3 seperate commands)
sudo apt-get update
```

edit - do 'apt-get update' at the beginning as well

---

