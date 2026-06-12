---
title: "Ubuntu Server 20.04.1 server halts after ssh key generation"
date: 2020-08-07
forum: Installation &amp; Upgrades
---

### Post by ryandlarkin on 2020-08-07
I am wondering if anyone has seen or better yet solved this issue. While trying to install Ubuntu Server 20.04.1 as a clean install, the installer halts after the ssh hey generation. The last few lines read (stripping a bit of code from the front):

:Welcome to Ubuntu Server Installer!
:Above you will find SSH host keys and a random password set for the `installer` user. You can use these credentials to ssh-in and complete the installation. If you provided SSH keys in the cloud-init datasource, they were also provisioned to the installer user.
: If you have access to the graphical console, like TTY1 or HMC ASCII terminal you can complete the installation there too.

Pressing ctrl-alt-f2 (3,4,5,6,7,8,9,0 whatever) is just a blank page with a blinking cursor which allows no input.

SSH works with the keys it lists, but then immediately crashes with the following output:

Traceback (most recent call last):
  File "/snap/subiquity/1966/usr/bin/subiquity", line 33, in <module>
    sys.exit(load_entry_point('subiquity==0.0.5', 'console_scripts', 'subiquity-tui')())
  File "/snap/subiquity/1966/lib/python3.6/site-packages/subiquity/cmd/tui.py", line 211, in main
    subiquity_interface.run()
  File "/snap/subiquity/1966/lib/python3.6/site-packages/subiquity/core.py", line 276, in run
    super().run()
  File "/snap/subiquity/1966/lib/python3.6/site-packages/subiquitycore/core.py", line 676, in run
    self.urwid_loop.run()
  File "/snap/subiquity/1966/usr/lib/python3/dist-packages/urwid/main_loop.py", line 286, in run
    self._run()
  File "/snap/subiquity/1966/usr/lib/python3/dist-packages/urwid/main_loop.py", line 384, in _run
    self.event_loop.run()
  File "/snap/subiquity/1966/usr/lib/python3/dist-packages/urwid/main_loop.py", line 1484, in run
    reraise(*exc_info)
  File "/snap/subiquity/1966/usr/lib/python3/dist-packages/urwid/compat.py", line 58, in reraise
    raise value
  File "/snap/subiquity/1966/usr/lib/python3.6/asyncio/events.py", line 145, in _run
    self._callback(*self._args)
  File "/snap/subiquity/1966/lib/python3.6/site-packages/subiquitycore/async_helpers.py", line 26, in _done
    fut.result()
  File "/snap/subiquity/1966/lib/python3.6/site-packages/subiquitycore/context.py", line 142, in decorated_async
    return await meth(self, **kw)
  File "/snap/subiquity/1966/lib/python3.6/site-packages/subiquity/controllers/refresh.py", line 151, in configure_snapd
    subcontext.description = "switched to " + channel
TypeError: must be str, not NoneType
Connection to [10.40.10.153]("callto:10.40.10.153") closed.

Has anyone seen this or have any idea what is causing it?

---

### Post by TheFu on 2020-08-07
Is this the amd64 installer or one of the lesser-used CPU or some "cloudy" specific install?

Looks like snap is the problem again, perhaps the snap or the settings for snaps in apparmor need fixing?
Doing a 20.04 server install using the newest subiquity now.  The ssh server keys were generated the step just before the option to update the installer was provided.

But I nearly cried tears of joy seeing the LVM management in the new installer. OMG - I've dreamed about this!

Start Install: Fri Aug  7 13:55:06 EDT 2020
[LIST]
[*]New subiquity
[*]Updates during install 
[*]Install openssh-server only, nothing else
[/LIST]
First Boot: Fri Aug  7 14:10:16 EDT 2020

So, I didn't see it on the media provided by 20.04.  I'll pull the 20.04.1 AMD64 server down tonight.

---

### Post by TheFu on 2020-08-07
On the login screen, there are a number of overflow ssh-related crap spewing where a userid and password belong.
In the hurry to get to a login screen, seems this other crap is leaking onto the console.  That only happened the 1st reboot. Later boots don't do this.

Plus, the "updates during install" appear not to have actually done updates during install.
```
58 updates can be installed immediately.
0 of these updates are security updates.
To see these additional updates run: apt list --upgradable
```

The good news is RAM use seems ok:
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:          981Mi       **119Mi**       617Mi       0.0Ki       244Mi       719Mi
Swap:         1.7Gi          0B       1.7Gi

```
No swap LV!  They created a 1.7G swap file.  That sucks.
Not thrilled with the fstab pointing at /dev/disk/by-id/dm-uuid-LVM-FTpkdBKYEm69SayhZQBt8DcwyZAdFYAmVv7pzXZKPoa1EQspo3K5QFIez1AgGvb for my root LV.  /dev/ubuntu-vg/ubuntu-lv certainly is nicer. Would love to know who thought that long dm-uuid-LVM-...... crap up.  Are they trying to make an fstab scary?

I'm a little uncertain why they installed lxd by default:
```
$ snap list
Name    Version   Rev    Tracking         Publisher   Notes
core18  20200311  1705   latest/stable    canonical&#10003;  base
lxd     4.0.1     14804  latest/stable/&#8230;  canonical&#10003;  -
snapd   2.44.3    7264   latest/stable    canonical&#10003;  snapd
```

The full-upgrade did what it should:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu **20.04.1 LTS**
Release:        20.04
Codename:       focal

```
so appears that using the 20.04 media could be a workaround.

---

