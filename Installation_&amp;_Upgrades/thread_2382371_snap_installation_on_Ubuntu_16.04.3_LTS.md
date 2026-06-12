---
title: "snap installation on Ubuntu 16.04.3 LTS"
date: 2018-01-12
forum: Installation &amp; Upgrades
---

### Post by senkum on 2018-01-12
Hi,

I am trying to install hello snap app given in the below link in Ubuntu 16.04.3 LTS machine, but i am getting http connection timeout error given below when i try to install hello snap. i have configured 
http_proxy in env as well. Please let me know your comments.

1> Link: [https://docs.snapcraft.io/build-snaps/your-first-snap](https://docs.snapcraft.io/build-snaps/your-first-snap)

2> Error:

```
root@cibu-desktop:/home/cibu/sendil/SNAP_TEST/snap# snap install hello_2.10_amd64.snap --dangerous
error: cannot perform the following tasks:
- Ensure prerequisites for "hello" are available (Get https://api.snapcraft.io/api/v1/snaps/details/core?channel=stable&fields=anon_download_url%2Carchitecture%2Cchannel%2Cdownload_sha3_384%2Csummary%2Cdescription%2Cdeltas%2Cbinary_filesize%2Cdownload_url%2Cepoch%2Cicon_url%2Clast_updated%2Cpackage_name%2Cprices%2Cpublisher%2Cratings_average%2Crevision%2Cscreenshot_urls%2Csnap_id%2Clicense%2Cbase%2Csupport_url%2Ccontact%2Ctitle%2Ccontent%2Cversion%2Corigin%2Cdeveloper_id%2Cprivate%2Cconfinement%2Cchannel_maps_list: net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers))
root@cibu-desktop:/home/cibu/sendil/SNAP_TEST/snap#
```

3> proxy settings in env:

```
root@cibu-desktop:/home/cibu/sendil/SNAP_TEST# env | grep proxy
http_proxy=proxy-wsa.esl.com
https_proxy=proxy-wsa.esl.com
root@cibu-desktop:/home/cibu/sendil/SNAP_TEST#
```



4> sancraft.yaml file:

```
root@cibu-desktop:/home/cibu/sendil/SNAP_TEST/snap# cat snapcraft.yaml 


name: hello
version: "2.10"
summary: GNU Hello, the "hello world" snap
description: GNU Hello prints a friendly greeting.
grade: stable
confinement: strict


apps:
  hello:
    command: hello


parts:
  gnu-hello:
    plugin: autotools
    source: http://ftp.gnu.org/gnu/hello/hello-2.10.tar.gz
root@cibu-desktop:/home/cibu/sendil/SNAP_TEST/snap#
```


Thanks,
Sendil

---

### Post by DuckHook on 2018-01-12
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by senkum on 2018-01-17
Error message:
```
root@cibu-desktop:/home/cibu/sendil/SNAP_TEST/snap# snap install hello_2.10_amd64.snap --dangerous
error: cannot perform the following tasks:
- Ensure prerequisites for "hello" are available (Get https://api.snapcraft.io/api/v1/snaps/details/core?channel=stable&fields=anon_download_url%2Carchitecture%2Cchannel%2Cdownload_sha3_384%2Csummary%2Cdescription%2Cdeltas%2Cbinary_filesize%2Cdownload_url%2Cepoch%2Cicon_url%2Clast_updated%2Cpackage_name%2Cprices%2Cpublisher%2Cratings_average%2Crevision%2Cscreenshot_urls%2Csnap_id%2Clicense%2Cbase%2Csupport_url%2Ccontact%2Ctitle%2Ccontent%2Cversion%2Corigin%2Cdeveloper_id%2Cprivate%2Cconfinement%2Cchannel_maps_list: net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers))
root@cibu-desktop:/home/cibu/sendil/SNAP_TEST/snap#


```

---

