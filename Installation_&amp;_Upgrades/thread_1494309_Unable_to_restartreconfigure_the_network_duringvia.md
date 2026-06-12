---
title: "Unable to restart/reconfigure the network during/via a preseed install"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by chienpo on 2010-05-26
**[SIZE=3]Background:[/SIZE]**

Hi, I'm installing an ubuntu server (10.04) system using my own custom preseed files.

The method I'm using is as follows:
[LIST=1]
[*]Boot from ubuntu-server install CD
[*]Select Language
[*]Press F6 so I can edit the "Boot Options"
[*]Enter the following boot parameters: "*auto=true priority=critical hostname=test  url=http://myserver.tld/seeds/default initrd=/install/initrd.gz quiet -- *"
[*]Boot...
[/LIST]
This causes the install to delay asking me about my language, country, and/or keyboard settings until after it **a)** sets up the network and **b)** downloads my custom preseed file.

My file is hosted on my server ([http://myserver.tld/seeds/](http://myserver.tld/seeds/)_default_) and is named "_default_". This gets downloaded just fine. For now its one and only action is to then load yet another preseed file based on the current _$hostname_ setting (_test_ in this case). This also works and [http://myserver.tld/seeds/](http://myserver.tld/seeds/)_test_ is successfully downloaded.

The settings in the _test_ preseed file successfully set my language, country, keyboard, etc. so that I don't ever get prompted for them.

[SIZE=3]**The Problem:**[/SIZE]

At this point, in the _test_ preseed file I try to re-configure my network settings with a static IP. The ultimate idea is, of course, to be able to have host-specific preseed files that include the various server's basic static network settings. Using the information in the documentation [here]("https://help.ubuntu.com/10.04/installation-guide/i386/preseed-contents.html") it instructs me how to go about doing this. In summary, the document says that in order to re-configure my network settings (from the default DHCP settings it currently has to my static configuration) I need to create a script with these two commands in it:
```

killall.sh
netcfg

```Then, I just need to include a "*preseed/run*" entry that will download and run this script.

I created the script file and named it "_restart_" and placed it in the same location on my web server as my two seed files. I also added a _preseed/run_ entry in my _test_ preseed file after my static network settings. The file does get downloaded by the installer (I see it in my apache logs) and I'm assuming that it gets executed since the DHCP network settings get dropped.

*The problem* is that the '_netcfg_' utility in the script doesn't seem to bring the network back up and I can't figure out how to diagnose the problem. The install will continue working, pulling from the CD but the clock doesn't get updated via ntp, updates don't get downloaded from remote locations, and the network settings therefor never get written out. I even attempted to manuall run 'netcfg' in one of the virtual terminals (ALT-F2) during the install to see what I could see.

Reading the docs I found on 'netcfg' it appears that it first attempts to bring up the network using DHCP and if that fails then via static configuration (paraphrasing here). Therefore, I have to assume it does so by pulling its settings/configuration from the debconf settings (provided by the preseed file). I just don't know and it just doesn't work.

So, any ideas? Any preseed install experts out there that can help me? I'd sure appreciate it.

File: _[http://myserver.tld/seeds/default](http://myserver.tld/seeds/default)_
```

d-i preseed/include_command string echo $hostname

```File: _[http://myserver.tld/seeds/test](http://myserver.tld/seeds/test)_
```

d-i debian-installer/locale string en_US
d-i console-setup/layoutcode string us
d-i console-setup/ask_detect boolean false
d-i netcfg/disable_dhcp boolean true
d-i netcfg/confirm_static boolean true
d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string test
d-i netcfg/get_domain string otherdomain.tld
d-i netcfg/get_gateway string 192.168.56.1
d-i netcfg/get_ipaddress string 192.168.56.10
d-i netcfg/get_netmask string 255.255.255.0
d-i netcfg/get_nameservers string 192.168.100.1
d-i preseed/run string restart

```File: _[http://myserver.tld/seeds/restart](http://myserver.tld/seeds/restart)_
```

killall.sh
netcfg

```File: apache.access.log
```

192.168.100.58 - - [26/May/2010:17:02:30 -0700] "GET /seeds/default HTTP/1.1" 200 50 "-" "Wget"
192.168.100.58 - - [26/May/2010:17:02:31 -0700] "GET /seeds/test HTTP/1.1" 200 1572 "-" "Wget"
192.168.100.58 - - [26/May/2010:17:02:41 -0700] "GET /seeds/restart HTTP/1.1" 200 18 "-" "Wget"

```

---

