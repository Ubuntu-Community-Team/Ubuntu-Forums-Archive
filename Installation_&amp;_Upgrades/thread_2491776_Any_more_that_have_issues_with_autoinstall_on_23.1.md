---
title: "Any more that have issues with autoinstall on 23.10.1?"
date: 2023-10-20
forum: Installation &amp; Upgrades
---

### Post by Jaxilian on 2023-10-20
Hi
I wonder if more are having issues with 23.10.1 regarding autoinstall. I had a nice working autoinstall setup that worked good with 23.04 and now when trying that same user-data file with 23.10.1 it fails every time. I pinned it down so it must be something with the late-command section cause that's where it fails.

just have a few of these lines pointing to various scripts

```
- curtin in-target -- bash /opt/scripts/post-install.sh
```

I have command prior to that which copies the scripts over first and if I don't include the lines like the one above, everything works and the scripts and the packages are there. I can even run them by themselves individually.
Did Canonical change something regarding autoinstall? maybe hired a different team for it with this version?
Cause it seems very odd

---

### Post by MAFoElffen on 2023-10-20
I haven't noticed any changes in autoinstall between 23.04 and 23.10. I don't know. I know there's a lot of the new examples in 
```

ubuntu@ubuntu:~/Downloads$ ls /snap/ubuntu-desktop-installer/1[0-9][0-9][0-9]/usr/share/doc/*/examples/
/snap/ubuntu-desktop-installer/1267/usr/share/doc/cloud-init/examples/:
cloud-config-add-apt-repos.txt         cloud-config-wireguard.txt
cloud-config-ansible-controller.txt    cloud-config-write-files.txt
cloud-config-ansible-managed.txt       cloud-config-yum-repo.txt
cloud-config-ansible-pull.txt          cloud-config.txt
cloud-config-apt.txt                   include-once.txt
cloud-config-archive-launch-index.txt  include.txt
cloud-config-archive.txt               kernel-cmdline.txt
cloud-config-boot-cmds.txt             network-config-v1-bonded-pair.yaml
cloud-config-ca-certs.txt              network-config-v1-bonded-vlan.yaml
cloud-config-chef-oneiric.txt          network-config-v1-bridge.yaml
cloud-config-chef.txt                  network-config-v1-multiple-vlan.yaml
cloud-config-datasources.txt           network-config-v1-nameserver.yaml
cloud-config-disk-setup.txt            network-config-v1-physical-3-nic.yaml
cloud-config-gluster.txt               network-config-v1-physical-dhcp.yaml
cloud-config-install-packages.txt      network-config-v1-route.yaml
cloud-config-launch-index.txt          network-config-v1-subnet-dhcp.yaml
cloud-config-lxd.txt                   network-config-v1-subnet-multiple.yaml
cloud-config-mount-points.txt          network-config-v1-subnet-routes.yaml
cloud-config-ntp.txt                   network-config-v1-subnet-static.yaml
cloud-config-reporting.txt             network-config-v1-vlan.yaml
cloud-config-run-cmds.txt              part-handler-v2.txt
cloud-config-ssh-keys.txt              part-handler.txt
cloud-config-update-apt.txt            plain-ignored.txt
cloud-config-update-packages.txt       seed
cloud-config-user-groups.txt           user-script.txt

/snap/ubuntu-desktop-installer/1267/usr/share/doc/grub-common/examples/:
grub.cfg

/snap/ubuntu-desktop-installer/1267/usr/share/doc/python3-aiohttp/examples/:
__init__.py          lowlevel_srv.py   web_rewrite_headers_middleware.py
background_tasks.py  server.crt        web_srv.py
cli_app.py           server.csr        web_srv_route_deco.py
client_auth.py       server.key        web_srv_route_table.py
client_json.py       server_simple.py  web_ws.py
client_ws.py         static_files.py   websocket.html
curl.py              web_classview.py
fake_server.py       web_cookies.py

/snap/ubuntu-desktop-installer/1267/usr/share/doc/python3-debian/examples/:
changelog  copyright  deb822  debfile  debtags

/snap/ubuntu-desktop-installer/1267/usr/share/doc/python3-serial/examples/:
at_protocol.py     setup-miniterm-py2exe.py        wxSerialConfigDialog.py
port_publisher.py  setup-rfc2217_server-py2exe.py  wxSerialConfigDialog.wxg
port_publisher.sh  setup-wxTerminal-py2exe.py      wxTerminal.py
rfc2217_server.py  tcp_serial_redirect.py          wxTerminal.wxg

/snap/ubuntu-desktop-installer/1267/usr/share/doc/python3-typing-extensions/examples/:
test_typing_extensions.py

/snap/ubuntu-desktop-installer/1267/usr/share/doc/python3-yaml/examples/:
pygments-lexer  yaml-highlight

```
But I honestly haven't had time to read thorugh those yet, except for the zfs autoinstall.yaml files

Do any of those help?

---

### Post by Jaxilian on 2023-10-20
thank you
I forgot to mention, it's the desktop version of Ubuntu. I tried even with just a very simple bashscript which only does **apt update** and **apt upgrade -y** or just install some small package like vlc, but that fails too. Same script works on 23.04. I have no idea what is wrong. I tried finding logs for this, but can't find the right one that shows the autoinstall installation process.

on the desktop version I don't have the path you showed to the examples (/snap/ubuntu-desktop-installer)

---

### Post by MAFoElffen on 2023-10-20
After booted, it's within the Live Image Environment (LIE), after the Snap ubuntu-desktop-installer is mounted into the filesystem. the center wildcard is the ubuntu-desktop-installer version... Until that mounts. it's only a partial mount tag there. If you update the installer Git version, it add another version path at the part of the directory structure...

Let me look what is there after an install... Not there. Only there when you boot into the LIE using "Try." Then that snap, 'ubuntu-desktop-installer' is mounted into the system at part of that path.

Yes, they are not documented. I have some questions filed, both at Launchpad and the GitHub on the 'ubuntu-desktop-installer' asking where they are storing the installer choice information, so that they might be tweaked during an install, for ZFS options and drive size tweaking... We used to be able to toggle over to a console tty. or terminal session to do that pre- 23.XX, but can't find where yet with 23.XX... That and a bug filed on how it creates recovery keys for LUKS in the new TPM backed Encrypted scripts, for potential lockouts.

Those were what I found when I was helping DEV test Mantic, and searching for my own answers.

---

### Post by MAFoElffen on 2023-10-21
I forgot to say, I have the git cloned and the examples are there also... for example one of the ones I mentioned "ai-zfs-guided.yaml:
```

#cloud-config
autoinstall:
  version: 1

  identity:
    realname: ''
    hostname: ubuntu
    username: ubuntu
    password: '$6$wdAcoXrU039hKYPd$508Qvbe7ObUnxoj15DRCkzC3qO7edjH0VV7BPNRDYK4QR8ofJaEEF2heacn0QgD.f8pO8SNp83XNdWG6tocBM1'

  source:
    id: ubuntu-server-minimal

  early-commands:
    - apt-get install -y zfsutils-linux

  late-commands:
    # Let's avoid recreating LP: #1993318
    - zpool set cachefile= rpool
    - cp /etc/zfs/zpool.cache "/target/etc/zfs/"
    - mkdir -p "/etc/zfs/zfs-list.cache" "/target/etc/zfs/zfs-list.cache"
    - truncate -s 0 /etc/zfs/zfs-list.cache/rpool
    - >-
      env -i
      ZEVENT_POOL=rpool
      ZED_ZEDLET_DIR=/etc/zfs/zed.d
      ZEVENT_SUBCLASS=history_event
      ZFS=zfs
      ZEVENT_HISTORY_INTERNAL_NAME=create
      /etc/zfs/zed.d/history_event-zfs-list-cacher.sh
    - >-
      sh -c
      'sed -E "s|\t/target/?|\t/|g" "/etc/zfs/zfs-list.cache/rpool" > "/target/etc/zfs/zfs-list.cache/rpool"'
    - rm -f "/etc/zfs/zfs-list.cache/rpool"

  storage:
    layout:
      name: zfs

```
Notice the format of the commands there in  early-commands and late-commands?

---

### Post by Jaxilian on 2023-10-23
Thanks, I found the examples
I can't figure out why my late commands are not working. It's just simple bash scripts that worked perfectly on 23.04...why not with 23.10? It's like the curtin command isn't there anymore. I am sorta testing on the those versions for the upcoming 24.04 LTS, trying to catch up as much as possible with the new installer.

I am one of two techs here at my university that is pushing for a Ubuntu platform, the other guy is learning Landscape at the moment. We need to come up with a PoC for the management to be able to get funding for the project (buying licenses and so on). The older debian based installer was easier to get working. Using that at the moment for 22.04.3.

---

### Post by Jaxilian on 2023-10-23
even tried a different format, like stated in link: [https://www.pugetsystems.com/labs/hpc/ubuntu-22-04-server-autoinstall-iso/]("https://www.pugetsystems.com/labs/hpc/ubuntu-22-04-server-autoinstall-iso/")

```
- curtin in-target --target /target bash /opt/scripts/post-install.sh
```

even though it says on [https://ubuntu.com/server/docs/install/autoinstall-reference]("https://ubuntu.com/server/docs/install/autoinstall-reference") (won't work either, I tried that too)

> late-commands
type: command list
default: no commands
can be interactive: no

Shell commands to run after the install has completed successfully and any updates and packages installed, just before the system reboots. They are run in the installer environment with the installed system mounted at /target. You can run curtin in-target -- $shell_command (with the version of subiquity released with 20.04 GA you need to specify this as curtin in-target --target=/target -- $shell_command) to run in the target system (similar to how plain in-target can be used in d-i preseed/late_command).

---

### Post by MAFoElffen on 2023-10-23
With 23.04, I followed Puget Sound System's instructions also, but I had to tweak the timing of that a little. On some things that I wanted to happen late, they wouldn't work either. 

I moved them to happen after the first reboot. I created a cloud-config.yaml and wrote it to an iso image, which I had there for the machine to see on boot... Those seemed to work there. 

I haven't had to chance to try that yet with 23.10.

---

### Post by Jaxilian on 2023-10-23
Here is what my user-data looks like

```
#cloud-config
autoinstall:
  version: 1
  refresh-installer:
          update: yes
  keyboard:
    layout: se
  locale: en_US.UTF-8
  timezone: Europe/Stockholm
  identity:
    hostname: unassigned-hostname
    username: ubuntu
    password: ubuntu (not the real one)
  source:
    search_drivers: true
    id: ubuntu-desktop-minimal
  storage:
    layout:
      name: direct
  updates: all
  late-commands:
    - mkdir /target/opt/packages
    - mkdir /target/opt/scripts 
    - cp -r /cdrom/packages /target/opt
    - cp -r /cdrom/nocloud/scripts /target/opt
    - curtin in-target -- bash /opt/scripts/post-install1.sh
    - curtin in-target -- bash /opt/scripts/post-install2.sh
    - curtin in-target -- bash /opt/scripts/post-install3.sh
```

within those postinstall-scripts are just some basic bash code to install some packages from repos and some custom debs. This is the setup that worked on Ubuntu 23.04 desktop.
Any suggestion that I can try? 
I notice on Ubuntu 23.04 with this setup, the installer says its completed before the late-commands have finished. It works on them in the background, but visually you get tricked to forcefully reboot the computer and it will break the installation. If I just let it sit, it will reboot after a while and everything is well.

---

### Post by MAFoElffen on 2023-10-23
> **Jaxilian said:**
> Here is what my user-data looks like

```
#cloud-config
autoinstall:
  version: 1
  refresh-installer:
          update: yes
  keyboard:
    layout: se
  locale: en_US.UTF-8
  timezone: Europe/Stockholm
  identity:
    hostname: unassigned-hostname
    username: ubuntu
    password: ubuntu (not the real one)
  source:
    search_drivers: true
    id: ubuntu-desktop-minimal
  storage:
    layout:
      name: direct
  updates: all
  late-commands:
    - mkdir /target/opt/packages
    - mkdir /target/opt/scripts 
    - cp -r /cdrom/packages /target/opt
    - cp -r /cdrom/nocloud/scripts /target/opt
    - curtin in-target -- bash /opt/scripts/post-install1.sh
    - curtin in-target -- bash /opt/scripts/post-install2.sh
    - curtin in-target -- bash /opt/scripts/post-install3.sh
```

Any suggestion that I can try? 


Two ideas;

First is, I'm not sure of $PATH during the autoinstall, so I add path paths to my commands, if they are not internal commands. Reminiscent of what you have to do for cron. The curtin in-target command does the chroot (and bind mounts things from the host for you so scripts can run and find /proc /run /dev etc. But I'm not sure it can just find 'bash' without the full path to it,  so more like this
```

  late-commands:
    - mkdir /target/opt/packages
    - mkdir /target/opt/scripts
    - cp -r /cdrom/packages /target/opt
    - cp -r /cdrom/nocloud/scripts /target/opt
    - curtin in-target -- /usr/bin/bash /opt/scripts/post-install1.sh
    - curtin in-target -- /usr/bin/bash /opt/scripts/post-install2.sh
    - curtin in-target -- /usr/bin/bash /opt/scripts/post-install3.sh
```
Couldn't hurt, for the just-in-cases...

Second: An out of the box idea, I have done this also... I recursively set execute permissions the post install scripts. If you did that on the scripts you copy over the your /opt/scripts/ folder and just called them directly? Something like...
```

  late-commands:
    - mkdir /target/opt/packages
    - mkdir /target/opt/scripts 
    - cp -r /cdrom/packages /target/opt
    - cp -r /cdrom/nocloud/scripts /target/opt
    - chmod -R 700 /opt/scripts
    - curtin in-target -- /opt/scripts/post-install1.sh
    - curtin in-target -- /opt/scripts/post-install2.sh
    - curtin in-target -- /opt/scripts/post-install3.sh

```
Ensuring the scripts had the full paths in the shabang's.

At this point, throwing out ideas that I've tried. The third is what I mentioned above, in the user-data of cloud-init on the first reboot, which looks like this
```

user-data:
  runcmd:
   - wget &#8230;.
   - chmod +x /path/to/script
   - /path/to/script
...

```

---

### Post by Jaxilian on 2023-10-24
```
- curtin in-target -- /usr/bin/bash /opt/scripts/post-install1.sh
```
all scripts have the path in the shebang and 700 set on rights. This fails

```
- curtin in-target -- /opt/scripts/post-install1.sh
``` 
This also fails

If I skip this line and just have until where it copies over the packages and scripts, it works and all the files are there with the correct rights. If I run the scripts manually then, they work fine automatically, but that won't do me any good cause nothing really gets installed the way I want.


it's like something is broken in 23.10.1
The runcmd: I try to avoid since where the commands is being executed. I need it to be within the installer, not after on first reboot.

---

### Post by MAFoElffen on 2023-10-24
File a bug against either subiquity or unbuntu-desktop-installer. <-- I'm not sure anymore which package currently. There's this gray area there now where we should file things on that. I would probably file it against 'subiquity' and let then sort it out.

There does seem to be a problem with that in 23.10.1, where it worked in 23.04. And there is no published changes in both of those that would account for that failing. Not that that process is documented for us very well anywhere.

I'm very curious at what they say, and find. Please post the Link to the Bug Report here so we can follow it. I'll bump it as "Also Affected" to add some weight to it, so they know it isn't isolated.

I have my own Bugs and questions filed against those... And am honestly frustrated at no responses. maybe because I keep my focus more towards some things that seem to want to ignore. I can't say that I have not had any responses. On some things the response and corrections were immediate. Others are still up there not even triaged. A question I have up there, I keep having to 'bump' to keep it from being changed to invalid from an expired timeout from no progress.

Maybe if we hit them from different angles and approaches, that something might happen(???) I'm still hoping.

---

### Post by Jaxilian on 2023-10-25
Thanks, but I have no clue on how to file a bug.

---

### Post by MAFoElffen on 2023-10-25
From a terminal or console session:
```

ubuntu-bug subiquity

```
It will start apport to start a bug report at Launchpad...
RE:  [Sticky: Improving Ubuntu: A Beginners Guide to Filing Bug Reports]("https://ubuntuforums.org/showthread.php?t=1011078")

I tell what I will do. Since I can replicate it, I will file the bug for you. Please join the bug as "It affects Me Also": [https://bugs.launchpad.net/subiquity/+bug/2040654](https://bugs.launchpad.net/subiquity/+bug/2040654)

---

### Post by MAFoElffen on 2023-10-25
The Bug Report has already been triaged and upgraded to critical. 

I worded it in a way that they should know that it affects their commercial support, and the current DEV cycle on Noble (which will be released as 24.04 LTS in April).

---

### Post by MAFoElffen on 2023-10-25
They are feverishly working on the fix. 

They know how they broke it (while trying to fix another Bug). LOL. I will tell you when they get the new Mantic ISO image done for us to test, to make sure the fix works. 

When verified that it is fixed, then they should release it publicly.

---

### Post by Jaxilian on 2023-10-26
> **MAFoElffen said:**
> They are feverishly working on the fix. 

They know how they broke it (while trying to fix another Bug). LOL. I will tell you when they get the new Mantic ISO image done for us to test, to make sure the fix works. 

When verified that it is fixed, then they should release it publicly.

Thank you so much.

---

### Post by MAFoElffen on 2023-10-28
They got back to me last night. They are making the change to the beta branch of the Snap ubuntu-desktop-installer...

Add this line into the refrsh-installer section to the autoinstall.yaml file
```

###
  refresh-installer: 
    update: yes
[COLOR=#ff0000]    channel: beta
[/COLOR]###

```
When they tell me it is ready to test, then test it... I'm still waiting of word for that. They told me about 24 hours on that.

Once verified, they can move it to stable, and we can change that "channel" line back to the "stable" branch... Or remove it. (the default without that line is the stable branch.)

---

### Post by MAFoElffen on 2023-11-06
I got a message saying this is ready to test from the beta channel...

---

### Post by Jaxilian on 2023-11-08
I will test as soon as I can

---

### Post by Jonners59 on 2023-11-08
> **Jaxilian said:**
> 

YES.  I'm having loads of issues on upgrading.  Two out of two not working.  Not had issues like this since 2013.  Not happy at all.

---

### Post by Jaxilian on 2023-11-08
> **MAFoElffen said:**
> I got a message saying this is ready to test from the beta channel...

Still doesn't work

Also I get different visual behaviour from the installer. I got it on the 23.04 as well. On 23.04 when the installer starts it could either be 1. just showing "preparing Ubuntu" throughout the whole installation process or 2. Showing the installer process like the normal way with the slides but it says it's finished before the late-commands starts and you have to wait until the automatic restart (even though the green button shows).
On 23.10 it shifts between showing like a 1. fullscreen "preparing Ubuntu" until error or a 2. split screen between the hotspot login and the installer showing " preparing Ubuntu" until error or 3. the normal installer window, but never finishes until error. It can shift between these even if I just change one thing in a script, like one word (no real obvious reason) 

I have to say the error message when the installer stops doesn't really say much to me as a user. I can't find what it complains about. The hotspot login window is a real pain to have, wish I could remove it completely from existance.

---

### Post by MAFoElffen on 2023-11-08
Could you run it, and instead of rebooting it... And (please) Upload the /var/log/installer/curtin-install.log to that bug report? We can show them what happened and tell them it still does not work...

---

### Post by Jaxilian on 2023-11-09
> **MAFoElffen said:**
> Could you run it, and instead of rebooting it... And (please) Upload the /var/log/installer/curtin-install.log to that bug report? We can show them what happened and tell them it still does not work...

cannot post it due to security token is missing :(

---

### Post by Jaxilian on 2023-11-09
However when I look into ubuntu_desktop_installer.log, I find this error "WARNING subiquity_server: Unable to find the subiquity_client_package. Falling back to the current working dir: /home/ubuntu""

---

### Post by Jaxilian on 2023-11-09
> **MAFoElffen said:**
> Could you run it, and instead of rebooting it... And (please) Upload the /var/log/installer/curtin-install.log to that bug report? We can show them what happened and tell them it still does not work...

OK I uploaded the info now to the bug report.

---

### Post by MAFoElffen on 2023-11-09
Thank you. I saw that. Since I started it ad am subscribed to it, whenever there is a update, I get an email on it. I get lots of emails, because I do DEV testing o the new releases, so tend to file a lot of Bugs. At some times 2-3 a day, then other times 1 in 2-3 months... Things just come up or happen.

Half the time, I wonder what they might be thinking when the see "another" bug report from me. LOL

---

### Post by Jaxilian on 2023-12-04
> **MAFoElffen said:**
> They got back to me last night. They are making the change to the beta branch of the Snap ubuntu-desktop-installer...

Add this line into the refrsh-installer section to the autoinstall.yaml file
```

###
  refresh-installer: 
    update: yes
[COLOR=#ff0000]    channel: beta
[/COLOR]###

```
When they tell me it is ready to test, then test it... I'm still waiting of word for that. They told me about 24 hours on that.

Once verified, they can move it to stable, and we can change that "channel" line back to the "stable" branch... Or remove it. (the default without that line is the stable branch.)

It seems to be working now. It goes through the full late commands scripts that I have. 
I have the **channel: beta** still though

---

### Post by MAFoElffen on 2023-12-04
Notified Dan that tested went well, and asked if he could move the changes from Beta to Stable.

---

### Post by Jaxilian on 2023-12-06
> **MAFoElffen said:**
> Notified Dan that tested went well, and asked if he could move the changes from Beta to Stable.

Thank you

Now I got another issue with the autoinstaller. I have separate grub menu option for manual choice on storage. If I add storage to interactive-sections to the user-data like

```
autoinstall:
   version: 1
   interactive-sections:
    - storage

```
it won't work, it first asks for network (which I didn't put in there) and then it actually freezes up the installer. There is no additional storage section in the user-data.
Am i doing something wrong?

I can't file a bug cause of it is data collecting from the computer. If there is a manual way I can do it.

---

### Post by MAFoElffen on 2023-12-06
That should have started interactive on the storage section(?) dang...

Here is one of my ZFS templates where I configure storage... But I initially configure NetPlan with dhcp4=true... Then go back later, and set to static, after the install for the specific machine.
```

    #cloud-config
    autoinstall:
      apt:
        disable_components: []
        geoip: true
        preserve_sources_list: false
        primary:
        - arches:
          - amd64
          - i386
          uri: http://archive.ubuntu.com/ubuntu
        - arches:
          - default
          uri: http://ports.ubuntu.com/ubuntu-ports
      drivers:
        install: false
      identity:
        hostname: HOSTNAME
        password: PASSWORD
        realname: USER
        username: USER
      kernel:
        package: linux-generic
      keyboard:
        layout: us
        toggle: null
        variant: ''
      locale: en_US.UTF-8
      network:
        ethernets:
          enp1s0:
            dhcp4: true
        version: 2
      ssh:
        allow-pw: true
        authorized-keys: []
        install-server: true
      storage:
        config:
        - ptable: gpt
          serial: 0QEMU_QEMU_HARDDISK_drive-scsi0
          path: /dev/sda
          wipe: superblock-recursive
          preserve: false
          name: ''
          grub_device: true
          type: disk
          id: disk1
        - device: disk1
          size: 1127219200
          wipe: superblock-recursive
          flag: boot
          number: 1
          preserve: false
          grub_device: true
          type: partition
          ptable: gpt
          id: disk1p1
        - fstype: fat32
          volume: disk1p1
          preserve: false
          type: format
          id: disk1p1fs1
        - path: /boot/efi
          device: disk1p1fs1
          type: mount
          id: mount-2
        - device: disk1
          size: -1
          wipe: superblock-recursive
          flag: root
          number: 2
          preserve: false
          grub_device: false
          type: partition
          id: disk1p2
        - id: disk1p2fs1
          type: format
          fstype: zfsroot
          volume: disk1p2
          preserve: false
        - id: disk1p2f1_rootpool
          mountpoint: /
          pool: rpool
          type: zpool
          device: disk1p2fs1
          preserve: false
          vdevs:
            - disk1p2fs1
        - id: disk1_rootpool_container
          pool: disk1p2f1_rootpool
          preserve: false
          properties:
            canmount: "off"
            mountpoint: "none"
          type: zfs
          volume: /ROOT
        - id: disk1_rootpool_rootfs
          pool: disk1p2f1_rootpool
          preserve: false
          properties:
            canmount: noauto
            mountpoint: /
          type: zfs
          volume: /ROOT/zfsroot
        - path: /
          device: disk1p2fs1
          type: mount
          id: mount-disk1p2
        swap:
          swap: 0
      early-commands:
        - "sudo apt-get install zfsutils-linux -y"
      updates: security
      version: 1

```

---

### Post by Jaxilian on 2023-12-07
If I put this

```
autoinstall:
   version: 1
   interactive-sections:
     - network
     - storage
```

then I get to choose network and storage and manually configure them (I have to click multiple times like its not getting the input), but as soon as I click to continue the screen goes grey (se attached file). If I switch from the QEMU VM to a real computer, then I don't get to see the storage section and it greyes out right after the network section.
I was hoping to get this working alongside with the other grub choices cause we have a lot of lab/instrument computers at the university that requires specific setups.

Every web page I read on internet about this topic, is for Ubuntu server and there everything seems fine and working with the above code. Just the Desktop version that seems to have been left behind...a lot.


update:
It's really hard to continue this work with getting autoinstall to work on 23.10. I get different variations from time to time even though I don't change anything. When I revert back to a user-data I know was functioning, it can give errors still (weird) I have the beta-flag still on the installer, but are there someone constantly changing the installer? Like every 30 min?
Sometimes the installer gets so it is not automatic at all, it wants manual input on every step even though I didn't change anything.

My hopes for this working in 24.04 LTS next year at the moment aren't high at all.

update again:

It seems like the software I partly was using for updating the image (cubic) is making the problems, or partly anyways. If I revert back to the script I had that just to opens the image, add all the files and user-data in it and close it, it works somewhat better. It still shows a different installer screen (Ubuntu 23.10.1 is installed and ready to use....with the green Restart now button), from the other when it is fully automatic (when the installer only says "Preparing Ubuntu" from start to finish).
It's gonna be tough to teach this different behaviour on the installer to my coworkers (Windows techs who is only gonna install it)

---

