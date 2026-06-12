---
title: "installing dapper 606"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by unisol on 2006-07-07
did a server install then tried to install ubuntu-desktop by way of apt partly installed returned message /usr/bin/dpkg returned error code 1 did apt-get -f install returned message process pre-installation script returned error code9

---

### Post by linear on 2006-07-07
[LEFT]Broken dependencies, perhaps? What does **apt-get check** tell you? The instructions [here]("http://www.ubuntuforums.org/showthread.php?t=186672") may help in resolving them.[/LEFT]

---

### Post by unisol on 2006-07-07
i dont know if this is the right thread but here goes i finally got it to boot to the login sreen i log in and the human theme appears but no taskbar or icons or menus

---

### Post by rcarring on 2006-07-07
You are missing some important packages

Try this:

Drop to the command line (exit the gui desktop).

```

sudo apt-get install metacity
sudo apt-get install nautilus nautilus-data

```

You need Nautilus properly installed in order to get the application bar and desktop icons working. I had exactly the same situation. Once you are running Nautilus (in GNOME) then use synaptic to make sure that the system knows nautilus is actually installed. If it shows up as not installed, mark for installtion and apply. If you are using kubuntu, somebody else would be able to help you.

---

### Post by unisol on 2006-07-12
i tried that and i got the mesage too many errors dpkg returned an error code1

---

### Post by linear on 2006-07-12
So have you tried the suggestions in the post [here]("http://www.ubuntuforums.org/showthread.php?t=186672")? It sounds like you still have dependency problems.

---

### Post by unisol on 2006-07-12
i tried again doing a resh install using both the graphical  and the alternate installer i have a syslog from the graphical installed:Error reading inode 5382.
Error reading inode 7035.
Error reading inode 7036.
Error reading inode 7037.
Error reading inode 7038.
Error reading inode 7039.
Error reading inode 7044.
Error reading inode 7045.
Error reading inode 7196.
Error reading inode 7214.
Error reading inode 7430.
Error reading inode 9397.
Error reading inode 9428.
Error reading inode 10175.
Error reading inode 10215.
Error reading inode 10227.
Error reading inode 10229.
Error reading inode 10231.
Error reading inode 10234.
Error reading inode 10246.
Error reading inode 10267.
Error reading inode 10375.
Error reading inode 10377.
Error reading inode 10385.
Error reading inode 10387.
Error reading inode 10391.
Error reading inode 10398.
Error reading inode 10431.
Error reading inode 10452.
Error reading inode 10618.
Error reading inode 10634.
Error reading inode 10797.
Error reading inode 11581.
Error reading inode 12318.
Error reading inode 12648.
Error reading inode 12651.
Error reading inode 12653.
Error reading inode 12673.
Error reading inode 13106.
Error reading inode 13107.
Error reading inode 13187.
Error reading inode 13188.
Error reading inode 13218.
Error reading inode 13220.
Error reading inode 13254.
Error reading inode 13263.
Error reading inode 13539.
Error reading inode 13540.
Error reading inode 14325.
Error reading inode 14326.
Error reading inode 14367.
Error reading inode 14368.
Error reading inode 15107.
Error reading inode 15108.
Error reading inode 15157.
Error reading inode 15408.
Error reading inode 15673.
Error reading inode 15776.
Error reading inode 15778.
Error reading inode 15930.
Error reading inode 15977.
Error reading inode 15979.
Error reading inode 17313.
Error reading inode 17636.
Error reading inode 17807.
Error reading inode 17808.
Error reading inode 18424.
Error reading inode 18425.
Error reading inode 18426.
Error reading inode 18427.
Error reading inode 18428.
Error reading inode 18429.
Error reading inode 18430.
Error reading inode 18432.
Error reading inode 18442.
Error reading inode 18534.
Error reading inode 19071.
Error reading inode 19095.
Error reading inode 19436.
Error reading inode 19489.
Error reading inode 19490.
Error reading inode 19555.
Error reading inode 19556.
Error reading inode 19964.
Error reading inode 19966.
Error reading inode 20156.
Error reading inode 20319.
Error reading inode 20757.
Error reading inode 20809.
Error reading inode 20892.
Error reading inode 20893.
Error reading inode 20946.
Error reading inode 20947.
Error reading inode 21075.
Error reading inode 21515.
Error reading inode 21516.
Error reading inode 21582.
Error reading inode 21583.
Error reading inode 21605.
Error reading inode 21606.
Error reading inode 21643.
Error reading inode 21645.
Error reading inode 21945.
Error reading inode 21949.
Error reading inode 22085.
Error reading inode 22086.
Error reading inode 23873.
Error reading inode 23874.
Error reading inode 25160.
Error reading inode 25161.
Error reading inode 25460.
Error reading inode 25762.
Error reading inode 25763.
Error reading inode 25840.
Error reading inode 25842.
Error reading inode 26105.
Error reading inode 26250.
Error reading inode 26252.
Error reading inode 26586.
Error reading inode 26967.
Error reading inode 26969.
Error reading inode 27393.
Error reading inode 28137.
Error reading inode 28140.
Error reading inode 28141.
Error reading inode 29946.
Error reading inode 30137.
Error reading inode 30138.
Error reading inode 30173.
Error reading inode 30174.
Error reading inode 30605.
Error reading inode 30779.
Error reading inode 30780.
Error reading inode 31712.
Error reading inode 31713.
Error reading inode 31714.
Error reading inode 31754.
Error reading inode 31756.
Error reading inode 32465.
Error reading inode 32470.
Error reading inode 32654.
Error reading inode 32656.
Error reading inode 32795.
Error reading inode 33050.
Error reading inode 33078.
Error reading inode 33079.
Error reading inode 33279.
Error reading inode 33280.
Error reading inode 33314.
Error reading inode 33315.
Error reading inode 33405.
Error reading inode 33407.
Error reading inode 33463.
Error reading inode 33527.
Error reading inode 33529.
Error reading inode 33531.
Error reading inode 33601.
Error reading inode 33767.
Error reading inode 33768.
Error reading inode 34406.
Error reading inode 34408.
Error reading inode 34569.
Error reading inode 34572.
Error reading inode 34878.
Error reading inode 34879.
Error reading inode 36182.
Error reading inode 36195.
Error reading inode 36992.
Error reading inode 36993.
Error reading inode 37056.
Error reading inode 37231.
Error reading inode 37232.
Error reading inode 37283.
Error reading inode 37284.
Error reading inode 38255.
Error reading inode 38258.
Error reading inode 38378.
Error reading inode 38385.
Error reading inode 40108.
Error reading inode 40111.
Error reading inode 41245.
Error reading inode 41246.
Error reading inode 42110.
Error reading inode 42111.
Error reading inode 42346.
Error reading inode 42364.
Error reading inode 42366.
Error reading inode 42382.
Error reading inode 42383.
Error reading inode 42429.
Error reading inode 43023.
Error reading inode 43024.
Error reading inode 43112.
Error reading inode 43633.
Error reading inode 43634.
Error reading inode 43697.
Error reading inode 43890.
Error reading inode 43970.
Error reading inode 44067.
Error reading inode 44208.
Error reading inode 44209.
Error reading inode 44246.
Error reading inode 44247.
Error reading inode 44288.
Error reading inode 44289.
Error reading inode 45198.
Error reading inode 45199.
Error reading inode 45347.
Error reading inode 45348.
Error reading inode 49128.
Error reading inode 49129.
Error reading inode 49768.
Error reading inode 49769.
Error reading inode 51460.
Error reading inode 51461.
Error reading inode 53249.
Error reading inode 53250.
dumpe2fs 1.38 (30-Jun-2005)
Warning: Unable to open /dev/hdc read-write (Read-only file system).  /dev/hdc h as been opened read-only.
Error: Unable to open /dev/hdc - unrecognised disk label.
Wed, 12 Jul 2006 16:04:32 INFO     Step_before = stepPartAdvanced
Wed, 12 Jul 2006 16:04:34 INFO     switched to page stepPartMountpoints
Wed, 12 Jul 2006 16:04:34 INFO     Step_after = stepPartMountpoints
Wed, 12 Jul 2006 16:04:45 INFO     Step_before = stepPartMountpoints
Wed, 12 Jul 2006 16:04:45 INFO     mountpoints: {'/dev/hde1': ('/media/hde1', Fa lse, None), '/dev/hde3': ('/', True, None), '/dev/hde2': ('swap', True, None)}
ubiquity: Starting up '/bin/partman' for ubiquity.components.partman_commit.Part manCommit
ubiquity: Watching for question patterns ^partman/choose_partition$, ^partman/co nfirm.*, type:boolean, ERROR, PROGRESS
mkdir: cannot create directory `/var/lib/partman': File exists
unsupported
kernelmodules_basicfilesystems
kernelmodules_ext3
kernelmodules_jfs
kernelmodules_reiserfs
kernelmodules_xfs
umount_target
parted
dump
update_partitions
filesystems_detected
auto_mountpoints
autouse_swap
backup
Wed, 12 Jul 2006 16:05:04 INFO     switched to page stepReady
ubiquity: Starting up '['/usr/share/ubiquity/summary']' for ubiquity.components. summary.Summary
ubiquity: Watching for question patterns ^ubiquity/summary$
swapon: /dev/hde2: Device or resource busy
swapon: /dev/hde2: Device or resource busy
swapon: /dev/hde2: Device or resource busy
swapon: /dev/hde2: Device or resource busy
umount /target/
swapoff /dev/hde2
chroot: cannot run command `apt-get': No such file or directory
Wed, 12 Jul 2006 16:06:32 INFO     progress_loop()
ubiquity: Starting up '['/usr/share/ubiquity/install.py']' for ubiquity.componen ts.install.Install
ubiquity: Watching for question patterns ^.*/apt-install-failed$, CAPB, ERROR, P ROGRESS
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1185, in ?
    if Install().run():
  File "/usr/share/ubiquity/install.py", line 212, in run
    if not self.copy_all():
  File "/usr/share/ubiquity/install.py", line 383, in copy_all
    os.mkdir(targetpath, mode)
OSError: [Errno 5] Input/output error: '/target/usr/lib/klibc/bin'
ubiquity: ['/usr/share/ubiquity/install.py'] exited with code 1
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 741, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1029,  in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and  /var/log/syslog

ubuntu@ubuntu:~$ File "/usr/bin/ubiquity", line 130, in ?
bash: File: command not found
ubuntu@ubuntu:~$     install(sys.argv[1])
bash: syntax error near unexpected token `sys.argv[1]'
ubuntu@ubuntu:~$   File "/usr/bin/ubiquity", line 55, in install
bash: File: command not found
ubuntu@ubuntu:~$     ret = wizard.run()
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$   File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
bash: File: command not found
ubuntu@ubuntu:~$     self.process_step()
>   File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 741, in process_step
bash: syntax error near unexpected token `File'
ubuntu@ubuntu:~$     self.mountpoints_to_summary()
>   File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1029, in mountpoints_to_summary
bash: syntax error near unexpected token `File'
ubuntu@ubuntu:~$     self.progress_loop()
>   File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
bash: syntax error near unexpected token `File'
ubuntu@ubuntu:~$     raise RuntimeError, ("Install failed with exit code %s; see "
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and /var/log/syslog

---

