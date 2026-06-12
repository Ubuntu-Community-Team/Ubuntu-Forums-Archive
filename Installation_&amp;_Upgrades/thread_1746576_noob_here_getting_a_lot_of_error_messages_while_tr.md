---
title: "noob here getting a lot of error messages while trying to uninstall AVG"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by bruce2wayne on 2011-05-01
recently i installed Avast in my ubuntu and tried to uninstall it using the following command 

```
sudo apt-get remove avast4workstation
```but am getting a lot of error messages what should i do to solve this can anyone wlak me through the problem in a step by step manner which would be of great learning experience to me.

and the error messages are as follows:

```
shan@shan:~$ sudo apt-get remove avast4workstation
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package avast4workstation is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up dkimproxy (1.2-3) ...
addgroup: The group `dkimproxy' already exists as a system group. Exiting.
The system user `dkimproxy' already exists. Exiting.
 * Starting inbound DomainKeys-filter dkimproxy.in                                                                                                                      Unknown option: hostname
Usage:
      dkimproxy.in [options] LISTENADDR:PORT RELAYADDR:PORT
        smtp options:
          --conf_file=FILENAME
          --listen=LISTENADDR:PORT
          --relay=RELAYADDR:PORT
          --reject-error

        verification options:
          --reject-fail
          --hostname=HOSTNAME

        daemon options:
          --daemonize
          --user=USER
          --group=GROUP
          --pidfile=PIDFILE

      dkimproxy.in --help
        to see a full description of the various options

                                                                                                                                                                 [fail]
invoke-rc.d: initscript dkimproxy, action "start" failed.
dpkg: error processing dkimproxy (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of dtc-toaster:
 dtc-toaster depends on dkimproxy; however:
  Package dkimproxy is not configured yet.
dpkg: error processing dtc-toaster (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 dkimproxy
 dtc-toaster
E: Sub-process /usr/bin/dpkg returned an error code (1)
shan@shan:~$ 

```

---

