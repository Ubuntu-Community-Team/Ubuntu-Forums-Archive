---
title: "FreeRADIUS not working after upgrade to 24.04.01"
date: 2024-09-11
forum: Installation &amp; Upgrades
---

### Post by Steven_Wittwer on 2024-09-11
I am running a Virtual Machine with Ubuntu Server Edition 22.04 LTS.  It is running FreeRadius.  I updated to 24.04.01 last night and FreeRADIUS wouldn't start.  I ended up reverting to a snapshot, so I don't have a lot of info, but iirc, it said that it was 'masked' and 'dead'.

Did I do something wrong?

I have 2 RADIUS servers, and I don't want to upgrade either until I know what is up.  

Any help or direction would be great!  I know I don't have much to go on.  But if needed, I can re-upgrade 1 of them and get details.

[EDIT]: I have multiple other upgrades that went smoothly.  DNS, Caddy, and Omada servers are all working fine.

---

### Post by 1fallen on 2024-09-11
Well without seeing the real error shown from terminal it is very hard for any of us to guide you.

They did move "FreeRADIUS" to:
```
/etc/freeradius/3.0
/etc/freeradius/dictionary_overrides
```
Did you check there?
Only the "dictionary_overrides" folder has to be in "/etc/freeradius." The last time I used it.

My solution then was to simply "sudo chown freerad:freerad /etc/freeradius/3.0"
Then reload the service.

But without seeing why yours is not working, I'm just sharing my commonly seen errors with Up-Grades.

---

### Post by Steven_Wittwer on 2024-09-11
I appreciate the reply.  

I am 99.9% sure that when I looked, the /etc/freeradius folder was completely missing after the upgrade.  I may try the upgrade again and see what happens.  This particular RADIUS server is only used for 2 users.  

If things go badly again, is there some output that would be helpful?  I am not a Ubuntu noob, but with that said, I am far from an expert.  I can certainly post the status of the service.

---

### Post by 1fallen on 2024-09-11
Well it is nicer if we know from the timeline of the failure:
Maybe this after the upgrade:
```
systemctl status freeradius.service
```

And possibly "dmesg" and or "apparmor"

But I suspect your error might be along the lines as this:
```
Process: 264020 ExecStartPre=/usr/bin/radiusd -C (code=exited, status=1/FAILURE)
Or This
Failed to start FreeRADIUS high performance RADIUS server
```

I would first like to see this though after the upgrade:
```
journalctl -xeu freeradius.service

```
And This Please:
```
radiusd -X
```
I'll be on and offline today just a heads up.

This might help you as well: [https://wiki.archlinux.org/title/FreeRADIUS](https://wiki.archlinux.org/title/FreeRADIUS)

---

### Post by Steven_Wittwer on 2024-09-11
Thanks, and no worries on being on and off.  I just completed the upgrade.  I forgot that it did ask me if I wanted to keep my version of the config or update.  I chose 'N' (which is default) to keep my version.

Here is an ls -lh showing the /etc/freeradius folder completely gone:

```
swittwer@tbcmc-admin-radius-vm:/etc$ ls -lh
total 912K
....
-rw-r--r-- 1 root root       685 Jan  8  2022 e2scrub.conf
-rw-r--r-- 1 root root       106 Feb 17  2023 environment
-rw-r--r-- 1 root root      1.9K Oct 17  2022 ethertypes
drwxr-xr-x 4 root root      4.0K Sep 11 10:14 fonts
-rw-r--r-- 1 root root       657 Nov  8  2023 fstab
-rw-r--r-- 1 root root       694 Mar 23  2022 fuse.conf
drwxr-xr-x 3 root root      4.0K Nov  8  2023 fwupd
-rw-r--r-- 1 root root      2.6K Feb  2  2022 gai.conf
drwxr-xr-x 2 root root      4.0K Sep 11 10:11 gnutls
drwxr-xr-x 2 root root      4.0K Sep 11 10:15 groff
....


```

```
swittwer@tbcmc-admin-radius-vm:/etc$ systemctl status freeradius.service
&#9675; freeradius.service
     Loaded: masked (Reason: Unit freeradius.service is masked.)
     Active: inactive (dead)
swittwer@tbcmc-admin-radius-vm:/etc$
```

The "journelctl" command had a bunch of empty lines ending in "-- No entries --"

[EDIT] I did a variety of dmesg commands (IE: dmesg | grep radius) and the only hit I got was the hostname.  no other references on radius, radiusd, or RADIUS.
[EDIT2] It scrolled by really fast, so I can't be 100% sure, but I think when the upgrade process was removing packages I saw a reference to freeradius.  It was so fast though that I am not 100% sure.  Obviously if that was the case, it would explain why it is missing.

---

### Post by 1fallen on 2024-09-11
The "journelctl" command had a bunch of empty lines ending in "-- No entries --" is because it's Masked??? Wired that's a first for me.

Have you tried to umask it?

Normally this should be the only entry's shown with:
```
 systemctl list-unit-files | grep masked
cryptdisks-early.service                                                  masked          enabled
cryptdisks.service                                                        masked          enabled
hwclock.service                                                           masked          enabled
saned.service                                                             masked          enabled
sudo.service                                                              masked          enabled
x11-common.service                                                        masked          enabled
zfs-import.service                                                        masked          enabled
zfs-load-key.service                                      
```
Maybe the above would be good to see as well.

Mine before the mask was issued:
```
systemctl status freeradius.service
&#9679; freeradius.service
     Loaded: masked (Reason: Unit freeradius.service is masked.)
     Active: active (running) since Wed 2024-09-11 12:32:36 MDT; 7min ago
 Invocation: 36f1889f57364628830ec5f291184a42
   Main PID: 68489 (freeradius)
     Status: "Processing requests"
      Tasks: 6 (limit: 16491)
     Memory: 42.2M (peak: 43.8M)
        CPU: 152ms
     CGroup: /system.slice/freeradius.service
             &#9492;&#9472;68489 /usr/sbin/freeradius -f

Sep 11 12:32:36 Legion-5-15ACH6-zfs freeradius[68487]: Compiling Auth-Type PAP for attr Auth-Type
Sep 11 12:32:36 Legion-5-15ACH6-zfs freeradius[68487]: Compiling Auth-Type CHAP for attr Auth-Type
Sep 11 12:32:36 Legion-5-15ACH6-zfs freeradius[68487]: Compiling Auth-Type MS-CHAP for attr Auth-Ty>
Sep 11 12:32:36 Legion-5-15ACH6-zfs freeradius[68487]: Compiling Autz-Type New-TLS-Connection for a>
Sep 11 12:32:36 Legion-5-15ACH6-zfs freeradius[68487]: Compiling Post-Auth-Type REJECT for attr Pos>
Sep 11 12:32:36 Legion-5-15ACH6-zfs freeradius[68487]: Compiling Post-Auth-Type Challenge for attr >
Sep 11 12:32:36 Legion-5-15ACH6-zfs freeradius[68487]: Compiling Post-Auth-Type Client-Lost for att>
Sep 11 12:32:36 Legion-5-15ACH6-zfs freeradius[68487]: radiusd: #### Skipping IP addresses and Port>
Sep 11 12:32:36 Legion-5-15ACH6-zfs freeradius[68487]: Configuration appears to be OK
Sep 11 12:32:36 Legion-5-15ACH6-zfs systemd[1]: Started freeradius.service - FreeRADIUS multi-proto
```

After a manual mask:
```
systemctl status freeradius.service
× freeradius.service
     Loaded: masked (Reason: Unit freeradius.service is masked.)
     Active: failed (Result: watchdog) since Wed 2024-09-11 12:40:38 MDT; 45s ago
   Duration: 7min 59.999s
 Invocation: 36f1889f57364628830ec5f291184a42
   Main PID: 68489 (code=dumped, signal=ABRT)
     Status: "Processing requests"
   Mem peak: 43.8M
        CPU: 191ms

Sep 11 12:32:36 Legion-5-15ACH6-zfs freeradius[68487]: Compiling Post-Auth-Type Client-Lost for attr Post-Auth-Type
Sep 11 12:32:36 Legion-5-15ACH6-zfs freeradius[68487]: radiusd: #### Skipping IP addresses and Ports ####
Sep 11 12:32:36 Legion-5-15ACH6-zfs freeradius[68487]: Configuration appears to be OK
Sep 11 12:32:36 Legion-5-15ACH6-zfs systemd[1]: Started freeradius.service - FreeRADIUS multi-protocol policy server.
Sep 11 12:40:06 Legion-5-15ACH6-zfs systemd[1]: freeradius.service: Got notification message from PID 68489, but reception is disabled
Sep 11 12:40:36 Legion-5-15ACH6-zfs systemd[1]: freeradius.service: Got notification message from PID 68489, but reception is disabled
Sep 11 12:40:36 Legion-5-15ACH6-zfs systemd[1]: freeradius.service: Watchdog timeout (limit 1min)!

```

Now I'll un mask it again:

First:
```
sudo syatemctl unmask freeradius.service
```
Reload systemd
```
sudo systemctl daemon-reload

```
Now try and start it:
```
systemctl start --now freeradius.service

```
Now check if its open for business.
```
systemctl status freeradius.service
&#9679; freeradius.service - FreeRADIUS multi-protocol policy server
     Loaded: loaded (/usr/lib/systemd/system/freeradius.service; enabled; preset: enabled)
     Active: active (running) since Wed 2024-09-11 12:32:36 MDT; 20s ago
 Invocation: 36f1889f57364628830ec5f291184a42
       Docs: man:radiusd(8)
             man:radiusd.conf(5)
             http://wiki.freeradius.org/
             http://networkradius.com/doc/
    Process: 68487 ExecStartPre=/usr/sbin/freeradius $FREERADIUS_OPTIONS -Cx -lstdout (code=exited,>
   Main PID: 68489 (freeradius)
     Status: "Processing requests"
      Tasks: 6 (limit: 16491)

```

---

### Post by Steven_Wittwer on 2024-09-11
I can do that (would have to update again, but that's easy).  However, based on my EDIT2 above, I checked to see if it was in fact removed, and it appears so.  I tried doing an apt install, and it said it was going to install all new packages.

I don't know why it would have been removed during the upgrade though.

---

### Post by 1fallen on 2024-09-11
> **Steven_Wittwer said:**
> 

I don't know why it would have been removed during the upgrade though.

Noble has had many surprises for myself and others,

Also check to see if these are intact as well:
```
sudo ls /etc/freeradius/3.0
certs          experimental.conf  mods-available  panic.gdb   radiusd.conf     sites-enabled   users
clients.conf  hints         mods-config     policy.d    README.rst       templates.conf
dictionary    huntgroups     mods-enabled     proxy.conf  sites-available  trigger.conf

```

Sounds like you might have a handle on this now, I'll check back later.

---

### Post by Steven_Wittwer on 2024-09-11
llike I mentioned, the /etc/freeradius folder is completely missing.  I suppose I can resinstall, and copy over my backups.

---

### Post by 1fallen on 2024-09-11
Yes I saw that. ;) This is after the upgrade and re-install of /freeradius .

If you do copy over from a back-up please let us know how that went for you.

---

### Post by Steven_Wittwer on 2024-09-11
It worked sorta.

On my phone, I had to reconnect and re-accept the cert since the new install had a new cert.  I only copied over the clients.conf and users file since that is all I needed.  

I want to avoid that when I do the staff Radius upgrade.  The staff will have no clue why it isn't working! I assume if I copy over the ca.cnf, client.cnf and server.cnf that I will be good?  Assuming so, who should the owner and permissions be set to?  I am not good with permissions in Ubuntu (other than basic stuff), so if there is a command I can use once I copy over the files, that would be great.

Again, really appreciate the help!

---

### Post by 1fallen on 2024-09-11
That's why I wanted an update on your copy over, Like I mentioned earlier 24.04 has had me on Toes with new changes, features New and Features Removed or breakage from bugs. :)
I can't see why the staff couldn't do the same though>> I love the "-a" switch when used with "cp"  it retains the permissions [U][B]from the user issuing the copy command.
> [/B][/U]-a, --archive                same as -dR --preserve=all

_****_

---

### Post by Steven_Wittwer on 2024-09-11
My server is a VM running on a Ubuntu host, so I used scp to copy them, but it still wiped out all permissions.  Not sure why.

---

### Post by 1fallen on 2024-09-11
> **Steven_Wittwer said:**
>  I used scp to copy them, but it still wiped out all permissions.  Not sure why.
There you go that's what I wanted to see. ;)
Replace: scp with rsync ie:
just a general showing so you will need to edit this to your needs:
```
rsync --perms --chmod=u+rwx,g+rwx,o+rwx /path/to/file server:/path/to/file

```

---

### Post by Steven_Wittwer on 2024-09-11
I'll try that in a bit.  when I tried rsync before (without all those options) it asked me for the root password on the device I was copying to.  Being Ubuntu, there wasn't a root user, so I wasn't able to complete it that way, but I will try again.

---

### Post by 1fallen on 2024-09-11
No Hurry take your time. And I assume you still have good back-ups.

---

### Post by Steven_Wittwer on 2024-09-11
What am I doing wrong?  I can add my username on the remote host, but that is what I did last time I did rsync, and permissions weren't copied.

```
swittwer@tbcmc-admin-radius-vm:~$ rsync --perms  --chmod=u+rwx,o+rwx /etc/freeradius/3.0/users 10.200.253.2:/home/swittwer/3.0
The authenticity of host '10.200.253.2 (10.200.253.2)' can't be established.
ED25519 key fingerprint is SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.200.253.2' (ED25519) to the list of known hosts.
swittwer@10.200.253.2's password:
rsync: [sender] link_stat "/home/swittwer/users" failed: No such file or directory (2)
skipping non-regular file "users"
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1338) [sender=3.2.7]


swittwer@tbcmc-admin-radius-vm:~$ sudo rsync --perms  --chmod=u+rwx,o+rwx /etc/freeradius/3.0/users 10.200.253.2:/home/swittwer/3.0
root@10.200.253.2's password:
Permission denied, please try again.
root@10.200.253.2's password:
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(713) [sender=3.2.7]
swittwer@tbcmc-admin-radius-vm:~$

```

---

### Post by 1fallen on 2024-09-11
Dang this is getting ridiculous, This worked for me the last I used it.....
I'm flat running out of ideas here:
On the VM what will this show:
```
#  stat /etc/freeradius/3.0
  File: /etc/freeradius/3.0
  Size: 21            Blocks: 18         IO Block: 1536   directory
Device: 0,28    Inode: 954746      Links: 9
Access: (0755/drwxr-xr-x)  Uid: (  132/ freerad)   Gid: (  140/ freerad)
Access: 2024-09-11 12:27:38.661218110 -0600
Modify: 2024-09-11 12:27:37.991218065 -0600
Change: 2024-09-11 12:27:38.659218110 -0600
 Birth: 2024-09-11 12:27:36.510217983 -0600
```

Someone else might need to jump in here, as I've taken all my servers off Buntu and replaced them with Arch and FreeBSD.

I'll try and recreate your system (VM) and test from there. But that will take some time, and probably tomorrow.

In the mean time anyone else is certainly welcome to jump in.

EDIT: Brain Fart Before I copied anything I did stop>>freeradius then made my "cp" or even "scp" the re-started all all the needed services.
 
```

sudo systemctl daemon-reload
```
And 
```

systemctl start --now freeradius.service
```

---

### Post by Steven_Wittwer on 2024-09-11
It might be easier just to see who the owner is of the cert files and try it out.  I just need to do some research to see if I can get the owner from the CLI (I'm sure I can, just not sure how yet).

[EDIT] easy enough... just ls -l.  They are root:root, so that should be easy to recreate.
[EDIT2] It's interesting though, in 22.04 most of the files/directories are freerad:freerad.

---

### Post by 1fallen on 2024-09-12
Well I was not able to reproduce what you have now, but this might be KEY, [COLOR=#E8E6E3] I did stop>>freeradius on the system copying to, .. then made my "cp" or even "scp" then re-started all all the needed services. See post #18[/COLOR]

---

### Post by Steven_Wittwer on 2024-09-12
Could be, but I at least know now how to recreate owner:group stuff and permissions.

Now my problem is that the certs aren't actually in the certs folder.  So I am not sure what to actually backup at this point.  I may just have to leave the staff Radius server as 22.04 for now.  I'll keep looking.

---

### Post by 1fallen on 2024-09-12
> **Steven_Wittwer said:**
>  I may just have to leave the staff Radius server as 22.04 for now.  I'll keep looking.

That sounds like a very wise choice for now....:)

---

### Post by cfrancis2000 on 2024-10-21
I inform you that the radius client does not work in Ubuntu 24.04 either (it does in 22.04).

---

