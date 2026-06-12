---
title: "Synaptic should tell you which PPA an update comes from!"
date: 2009-08-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-08-20
I use a lot of PPA sources and I'm sick and tired of seeing an update from a PPA and not being able to tell which PPA it comes from.

God forbid a conflict occurs. I wouldn't know which source to remove!

[https://bugs.launchpad.net/synaptic/+bug/416267](https://bugs.launchpad.net/synaptic/+bug/416267)

---

### Post by slakkie on 2009-08-20
I use the following script to see from which repo something is coming from. You could change it a bit to also show you the URL of the repo:

```

repo2pkg () {
        local repos=$@
        [ -z "$repos" ] && repos=$(lsb_release -cs)
        local pkg
        local cur
        local can
        local policy
        local repo
        local upgrade
        local _repo
        for pkg in $(dpkg -l | grep '^ii'| awk '{print $2}' )
        do
                upgrade=""
                policy=$(apt-cache policy $pkg)
                cur=$(echo -e "$policy" |  grep Installed | awk '{print $NF}')
                can=$(echo -e "$policy" |  grep Candidate | awk '{print $NF}')
                [ "$can" == "(none)" ] && can=$cur
                [ "$can" != "$cur" ] && upgrade=1
                for repo in $repos
                do
                        _repo=$(echo -e "$policy" | grep -A1 "$can" | grep -w "$repo" | awk '{print $2":"$3}')
                        if [ -n "$_repo" ]
                        then
                                for i in $_repo
                                do
                                        [ -n "$upgrade" ] && pkg="$pkg (UPDATE $cur => $can)"
                                        printf "%-55s %-20s\n" "$i" "$pkg"
                                done
                                break
                        fi
                done
        done
}

```

I need to upgrade curl on my current machine (as shown by aptitude -s safe-upgrade) and I would like to know where it will retreive the update from I can use the following:

```

apt-cache policy curl
curl:
  Installed: 7.18.0-1ubuntu2.1
  Candidate: 7.18.0-1ubuntu2.2
  Version table:
     7.18.0-1ubuntu2.2 0
        500 http://nl.archive.ubuntu.com hardy-updates/main Packages
        500 http://security.ubuntu.com hardy-security/main Packages
 *** 7.18.0-1ubuntu2.1 0
        100 /var/lib/dpkg/status
     7.18.0-1ubuntu2 0
        500 http://nl.archive.ubuntu.com hardy/main Packages

```

As you can see, hardy-updates and hardy-security both give me the package I will use to upgrade. A similar thing you will see when upgrading from your PPA.

---

