---
title: "Upgrade script which excludes kernel updates"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by madwoollything on 2009-11-30
Having just broken my wubi 9.10 installation by applying the latest kernel upgrade, I was wondering if it is possible to write a script to apply recommended updates but exclude any new kernel packages. 

I'm having to do this manually at present and it must be possible to automate this in Linux.

Any help would be much appreciated. Having read the man pages for apt-get & aptitude I'm still no wiser.

---

### Post by slakkie on 2009-11-30
man apt_preferences :)

```

pkg2pin () {
        [ -z "$1" ] && return
        local pkg
        local msg
        local prefs=/etc/apt/preferences
        msg="$(date +'%Y%m%d:%H%M%S')"
        for pkg in $@
        do
                pkg=$(dpkg -l "$pkg" 2>/dev/null)
                [ $? -ne 0 ] && continue
                pkg=$(echo -e "$pkg" | grep "^ii" |awk '{print $2" "$3}')
                echo -e "$pkg" | awk '{print "# Added on '$msg' by pkg2pin or dpkg2pin\nPackage: "$1"\nPin: version "$2"\nPin-Priority: 1001\n"}'
        done | sudo tee -a $prefs
}

dpkg2pin () {
        [ -z "$1" ] && return
        local pkg
        pkg=$(dpkg -l | grep "^ii" |awk '{print $2}' | grep "$1")
        [ $? -ne 0 ] && return
        for i in $pkg
        do
                pkg2pin $i
        done
}

```

Put that hunk of code in your .bashrc, reload bash or source the file and then:

dpkg2pin linux-image

This will add all the linux-image* packages into the preferences file, which will prevent updates for the kernels. You could also add the header files:

dpkg2pin linux-header

And done.


In action:

aptitude -s safe-upgrade

```

The following packages have been kept back:                                                     
  bootchart                                                                                     
The following packages will be upgraded:                                                        
  linux-headers-generic [2.6.31.15.28 -> 2.6.32.5.5]  linux-image-generic [2.6.31.15.28 -> 2.6.32.5.5]  
2 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.                                 

```

```

dpkg2pin linux-image-generic
# Added on 20091130:182542 by pkg2pin or dpkg2pin                                               
Package: linux-image-generic                                                                    
Pin: version 2.6.31.15.28                                                                       
Pin-Priority: 1001                                                                              

dpkg2pin linux-headers-generic 
# Added on 20091130:182548 by pkg2pin or dpkg2pin                            
Package: linux-headers-generic                                               
Pin: version 2.6.31.15.28                                                    
Pin-Priority: 1001                                                           

```


And now do the same upgrade:

aptitude -s safe-upgrade
```

The following packages have been kept back:
  bootchart
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

No kernel updates for you, if you decide that you want kernel upgrades again, delete the entries from /etc/apt/preferences.

---

### Post by madwoollything on 2009-12-01
Thanks ..... much appreciated

---

