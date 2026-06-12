---
title: "update manager won't get files after 9.10 upgrade"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by kevingtonbeare on 2009-12-21
I have just upgraded to Ubuntu 9.10 from Jaunty.

Firstly I could not access the internet from Firefox.  Fixed this by turning off ipv6 in Firefox. Can ping sites from the command line and network tools, can also do traceroutes.  However, the attempts to use the update manager results in a big delay, then messages like: 

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

I have tried blacklisting ipv6 in blacklist.conf, but this does not work.

Everything worked fine before the upgrade!

Cheers
KevingtonBeare

---

### Post by garvinrick4 on 2009-12-21
Are you accessing internet at this time?

---

### Post by kevingtonbeare on 2009-12-21
> **garvinrick4 said:**
> Are you accessing internet at this time?
Sorry, I do not understand the precise meaning of your question.  Of course trying to download updates from au.archive.ubuntu.com means that I am accessing, or attempting to access, the internet. If you mean "Can I access the internet?" then the answer is "Yes" - I can access sites worldwide via Firefox, I can use net tools and can ping and tracert from the command line in Terminal.  If you mean, "Are you simultaneously accessing the internet from the computer which is trying to download updates?" then the answer is, "No, not as far as I know. I do not have other desktops open, and I am not trying to run other internet accessing processes in the foreground."  If you mean, "Is anyone else on your home net work accessing the internet from their computer?" then the answer is, "Not as far as I know - I believe other members of the family were away from their computers at the time."

The problem seems, at this stage, localised to Update Manager - which worked OK under Jaunty and enabled me to download the update to 9.10, but since the upgrade to 9.10 was competed, I have not been able to use Update Manager.

Thank you for your interest and help
KevingtonBeare

---

### Post by kevingtonbeare on 2009-12-21
Further information:
1.  I tried to download the ntp package via apt-get install from the command line in Terminal, with the same result - not able to access the archive.
2.  I changed the archive server in the Update Manager options to two local Australian server, one an http server, the other an ftp server.  Again the same result.

Is anyone else having this problem?

In frustration,
KevingtonBeare

---

### Post by Dennis N on 2009-12-22
You might try disabling ipv6 for the entire system (not just Firefox) and see if that solves the problem. A way to do that is described here:

[http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html](http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html)

See the section immediately following the method for disabling it in Firefox only.

---

### Post by kevingtonbeare on 2009-12-22
> **Dennis N said:**
> You might try disabling ipv6 for the entire system (not just Firefox) and see if that solves the problem. A way to do that is described here:

[http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html](http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html)

See the section immediately following the method for disabling it in Firefox only.
Many thanks for the suggestion.  I followed your instructions, but when I ran ifconfig, it still showed an inet6 address attached to eth0.

So I used sudo ifconfig -v etho0 inet6 del <ipv6 address> then ran ifconfig again.  this showed that the ipv6 address was no longer attached to eth0.  I then tried Update Manager - with the same dismal results.

I am beginning to wonder if the problem is not ipv6 at all, but an archive server athentication issue.

Does anybody from Canonical/Ubuntu read these posts?

Regards to all,
KevingtonBeare

---

### Post by garvinrick4 on 2009-12-22
The only thing left is software sources to change your mirror. Here is a list of the Aussie
ones. System/admin/software sources/ ubuntu software tab to download from to custom.

Australia                        5 Gbps 8 mirrors
                        http ftp         One week
iiNet                            1 Gbps
                        rsync            behind
                                         One week
Netspace Online Systems http ftp 1 Gbps
                                         behind
                        http ftp
AARNet Pty Ltd                   1 Gbps One day behind
                        rsync
                        http ftp
Internode                        1 Gbps Up to date
                        rsync
                                         One week
Netspace Online Systems http     1 Gbps
                                         behind
                                         Two days
Optus.net               http     10 Mbps
                                         behind
                                         Two days
Mirror-pacific-net-au   http     10 Mbps
                                         behind
                                         One week
WAIA                    http ftp 10 Mbps
                                         behind

Pick the best one and choose in custom. reload or "sudo apt-get update" without qoutes

---

### Post by kevingtonbeare on 2009-12-22
> **garvinrick4 said:**
> The only thing left is software sources to change your mirror. Here is a list of the Aussie
ones. System/admin/software sources/ ubuntu software tab to download from to custom.

Australia                        5 Gbps 8 mirrors
                        http ftp         One week
iiNet                            1 Gbps
                        rsync            behind
                                         One week
Netspace Online Systems http ftp 1 Gbps
                                         behind
                        http ftp
AARNet Pty Ltd                   1 Gbps One day behind
                        rsync
                        http ftp
Internode                        1 Gbps Up to date
                        rsync
                                         One week
Netspace Online Systems http     1 Gbps
                                         behind
                                         Two days
Optus.net               http     10 Mbps
                                         behind
                                         Two days
Mirror-pacific-net-au   http     10 Mbps
                                         behind
                                         One week
WAIA                    http ftp 10 Mbps
                                         behind

Pick the best one and choose in custom. reload or "sudo apt-get update" without qoutes
Thanks again for your suggestion.  I tried two Aussie mirrors, an http mirror and an ftp mirror - same result - no downloads.

Nor does "sudo apt-get install <package_name>" work.

Surely to goodness I am not the only one having this problem?

Thanks again
KevingtonBeare

---

### Post by kevingtonbeare on 2009-12-22
OK, I changed the software sources to Main.
Tried to run Update Manager and it failed to download the 22 Package Information files.  I got the following errors:
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg](http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_AU.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_AU.bz2)  Unable to connect to archive.canonical.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_AU.bz2)  Unable to connect to archive.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

What do these error messages mean, and how do I correct the situation?

Thanks
KevingtonBeare

---

### Post by levelhead21 on 2010-04-28
I'm just a noob, so I'm not sure if this will work for you, but I had a similar problem where some of my last update could not be installed and since then my Update Manager says it cannot connect with the server to fetch my packages. What I did was click on SETTINGS (bottom left side of Update Manager). Then under the UBUNTU SOFTWARE tab, I changed the DOWNLOAD FROM selection to MAIN SERVER. It was previously set at CANADA. 46 packages were successfully uploaded and installed after that change.

---

