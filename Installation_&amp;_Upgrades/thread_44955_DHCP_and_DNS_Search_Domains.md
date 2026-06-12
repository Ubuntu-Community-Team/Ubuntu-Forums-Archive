---
title: "DHCP and DNS Search Domains"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by Ken.Lank on 2005-06-28
How do you permenantly add a DNS Search Domain in addition to the ones that DHCP assigns?

My DHCP server (not under my control) assigns domain_1.com through DHCP, but I also need domain_2.com added to my DNS Search Domain.  If I add this to the resolv.conf or through the "System...Administration...Networking" on the DNS tab I can get it to work, but on a reboot it reverts to just domain_1.com.  How can I append this additional search domain automatically to the DHCP results?

Thanks,
Ken

---

### Post by Ken.Lank on 2005-06-29
As an update.  I looked at what search names were assigned to my Windows machine and it did get assigned both.  Please help! ](*,)

---

### Post by mcduck on 2005-06-29
I had the same problem, myt ISP:s default DNS is _slow_, but they have another one that works nice. Adding this other DNS didn't work, as my settings got erased about every half hour. 

Anyway, I found out that these settings were reset by /etc/dhcp3/dhclient-script. As I'm not a linux-guru I didn't want to completely remove this script so I edited it and commented out lines that reset domain name servers. After that I've had no more problems: I'm still using DHCP but now I can manually edit DNS settings.

Here are the lines that I edited:

```

#        if [ -n "$new_domain_name_servers" ]; then
#            for nameserver in $new_domain_name_servers; do
#                echo nameserver $nameserver >>$new_resolv_conf
#            done
#        else # keep 'old' nameservers
            egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
                  $new_resolv_conf
#        fi

```

Hope this helps.

---

### Post by Ken.Lank on 2005-06-29
Thanks mcduck.  It exactly what I needed, but it pointed me to the right file.  I was able to modify this file to put the correct entries in. \\:D/

---

### Post by talen.quickblade on 2007-09-07
A much easier tweak would be to comment out the line where the new resolv.conf is moved over top of the old one. This will prevent the old file from being over written... ever (almost).

        mv -f $new_resolv_conf /etc/resolv.conf


After further exploration of the dhclient-script (mostly reading the man page and lots of blank stares later), I find out that hooks are available to over-ride the default behavior (which is to overwrite the file when the script gets called). One is not *supposed* to edit the dhclient-script file. Why?  Because as soon as a package updates dhclient... guess what is gonna happen. Your customization is gonna get over-written with the new package contents.

/etc/dhcp3/dhclient-enter-hooks allows you to re-define functions prior to the dhclient-script actually being called. Knowing this, and knowing that the function resulting in the resolv.conf being overwritten is "make_resolv_conf".  It should be a simple matter of just making a new simple function.

1) create the file
     sudo touch /etc/dhcp3/dhclient-enter-hooks
2) add the folloing text to the file
     make_resolv_conf() {
        echo "not touching resolv.conf because of enter hook"
        }
3) save and rejoice!

I hope this helps SOMEONE curtail the loss of hair I have experienced in fighting this thing.  I cant wait to get home and find out if it solves some other problems I am having on my home machine.

---

