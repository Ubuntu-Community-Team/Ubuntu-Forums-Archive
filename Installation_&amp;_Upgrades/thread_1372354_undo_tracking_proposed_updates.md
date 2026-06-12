---
title: "undo tracking proposed updates"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by 65 mustang on 2010-01-04
In the "software sources" windows under the "Updates" tab I have checked "Pre-released updates" and installed all the updates.  I no longer want to track the proposed updates and have unchecked that item.  Now am back to just security and recommended checked.  How do i get it to downgrade the packages that it has modified when I had "Pre-released" checked?  I want to get back on the stable "Recommended Updates".  It seems to have changed what it looks at for updates but did not downgrade the packages.  :confused:

---

### Post by slakkie on 2010-01-04
Apt never downgrades packages (by itself, you must tell it to do so).

Just wait a while. Or.. 

```

pkg2repo () {
        [ -z "$1" ] && return
        local pkg="$1"
        local policy
        local cur
        local can
        local upgrade
        for pkg in $@
        do
                policy=$(apt-cache policy $pkg)
                cur=$(echo -e "$policy" |  grep Installed | awk '{print $NF}')
                can=$(echo -e "$policy" |  grep Candidate | awk '{print $NF}')
                upgrade="$cur"
                [ "$can" == "(none)" ] && can=$cur
                [ "$can" != "$cur" ] && upgrade="U: $cur > $can"
                repos=$(echo -e "$policy" | grep "$can" -A1 | egrep "(http|ftp|smb|cdrom|nfs|file)://" | tail -1 | awk '{print $2" "$3}')
                local msg
                msg="%-35s %-45s %s\n"
                [ -n "$repos" ] && printf "$msg" "$pkg" "$upgrade" "$repos"
        done
}

repo2pkg () {
        local frepos=$@
        local repos
        for pkg in $(dpkg -l | grep '^ii'| awk '{print $2}' )
        do
                repos=$(pkg2repo $pkg)
                if [ -z "$frepos" ]
                then
                        [ -n "$repos" ] && echo -e "$repos"
                        continue
                fi
                for i in $frepos
                do
                        echo -e "$repos" | grep -w "$i"
                        [ $? -eq 0 ] && break
                done
        done
}

```

```

repo2pkg backports
alpine                              2.00+dfsg-1~hardy1                            http://archive.ubuntu.com hardy-backports/universe
apturl                              0.2.6ubuntu1~hardy1                           http://archive.ubuntu.com hardy-backports/main    
debhelper                           7.0.13ubuntu1~hardy1                          http://archive.ubuntu.com hardy-backports/main
debian-policy                       3.8.0.1~hardy1                                http://archive.ubuntu.com hardy-backports/universe
debootstrap                         1.0.20~hardy1                                 http://archive.ubuntu.com hardy-backports/main
devscripts                          2.10.39ubuntu2~hardy1                         http://archive.ubuntu.com hardy-backports/main

```

And then you can reinstall those packages:

```

for i in $(repo2pkg backports | awk '{print $1}') ; do
    sudo aptitude install $i/hardy
done

```

You need -proposed enabled otherwise the functions do not know which repo has them, obviously.

That will then reinstall all the packages to the main hardy repo. Then upgrade and you are good to go. 

Or just wait a few days, -proposed ends up in -updates so if you have that repo enabled just wait.

---

