---
title: "Upgrade to Ubuntu 9.04 has broken ebox, samba share no longer visible to users"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by laobhaise on 2009-12-04
Hi,

I am pretty new as a system administrator but the file server at my workplace needed to be upgraded from 8.04 to at least 9.04.

I did the upgrade in stages, first from 8.04 to 8.10. I noticed immediately that I could not longer access the ebox interface and on checking on the machine itself ebox seems to be broken. I was getting errors that dependencies hadn't been met and certain "libs" couldn't be installed...

However, I could still see the samba share from a client machine. At this point, maybe I lost my mind, but 8.10 seemed buggy to me and I thought 9.04 would be more stable.

On upgrading to 9.04 the situation to ebox did not improve and now I cannot access the samba share from any client machine!!!!

I have been trying to find a way to fix this for hours and hours... I have looked at ebox installation via the sources.list file. I have tried removing, reinstalling it...
fileserver@ngorc:/etc$ sudo apt-get install ebox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ebox: Depends: libebox (>= 1.3) but it is not going to be installed
        Depends: libebox (<= 1.4) but it is not going to be installed
        Depends: libgnome2-gconf-perl but it is not installable
        Depends: libsys-cpu-perl but it is not installable
        Depends: libsys-cpuload-perl but it is not installable
        Depends: libproc-process-perl but it is not installable
        Depends: libdbd-pg-perl but it is not installable
        Depends: libclone-perl but it is not installable
        Depends: libfilesys-df-perl but it is not installable
        Depends: libxml-rss-perl but it is not installable
        Depends: libyaml-tiny-perl but it is not installable
E: Broken packages


When I try to restart ebox I get the following error:

fileserver@ngorc:/etc$ sudo /etc/init.d/ebox restart
Can't locate EBox/Global.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /etc/init.d/ebox line 14.
BEGIN failed--compilation aborted at /etc/init.d/ebox line 14.

When I try to login as a user from a client machine to access the samba share the nautilius file browser just loops on requesting a password.

I looked at the smb.conf file and it looks ok to me, but it is configured with ebox parameters so if ebox is broken I'm not expecting it to work. 

I don't understand how the share was visible on upgrading to 8.10 even though ebox was broken at that stage and then completely inaccessible on upgrading to 9.04.

In desperation I tried smbclient command to list shares and I see nothing. I see nothing on the client machine for .gvfs and nothing when I run the command in a terminal.

I really have no idea at this point what to do to get the share back on line and visible to the users from a fileserver that is now Ubuntu 9.04, with a broken ebox install.

I have no idea what to do now to get everything back on track again... I just don't seem to have enough experience... and I would appreciate any help at all.. please!!!!

Thanks in advance,
laobhaise ](*,)

---

### Post by laobhaise on 2009-12-07
Just wondering if there is anyone at all who can give me any guidance or suggest some next steps... anything at all?

I would appreciate any help!

Many thanks and regards,
Laobhaise

---

