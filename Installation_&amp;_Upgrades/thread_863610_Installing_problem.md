---
title: "Installing problem"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by speculatius on 2008-07-18
I try to install Ubuntu 8.04, buy after 3th step of installation it stops with funny error "??? ???". I use toshiba satellite m100-221 and i've got winXP already installed. Before, I was running ubuntu 7.10 with no errors. Can you help me? Or do you understand that error message? :)

Thanks...

---

### Post by Pumalite on 2008-07-18
Burn a new CD. Do md5sum on the iso. Burn at 4x or less. Do not use CD-RW. Check CD integrity before you install.

---

### Post by jimv on 2008-07-18
What was the error message?

---

### Post by speculatius on 2008-07-19
First, thank for replies.

- i think, cd is good - i can run live distribution and do anything instead of going through step 3 of installation.

- the error message is "??? ???" and the title of this error-window is "??? ???" :)

- i tried to install Xubuntu 8.04 as well, but there was the same error

---

### Post by speculatius on 2008-07-19
EDIT: When I run installation from console, it write:

[I]
 *** stack smashing detected ***: parted_server terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7e36138]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7e360f0]
/lib/libparted-1.7.so.1[0xb7eeb5b4]
/lib/libparted-1.7.so.1[0xb7ebe388]
/lib/libparted-1.7.so.1[0xb7ebe2fe]
/lib/libparted-1.7.so.1[0xb7ebe2fe]
.
.
.
/lib/libparted-1.7.so.1[0xb7ebe2fe]
/lib/libparted-1.7.so.1[0xb7ebe2fe]
/lib/libparted-1.7.so.1(fat_collect_cluster_info+0xf1)[0xb7ebe481]
/lib/libparted-1.7.so.1(fat_open+0x17f)[0xb7ebfaff]
======= Memory map: ========
08048000-08057000 r-xp 00000000 07:00 101796     /rofs/bin/parted_server
08057000-08058000 rw-p 0000e000 07:00 101796     /rofs/bin/parted_server
08058000-08230000 rw-p 08058000 00:00 0          [heap]
b75a7000-b75b1000 r-xp 00000000 07:00 103711     /rofs/lib/libgcc_s.so.1
b75b1000-b75b2000 rw-p 0000a000 07:00 103711     /rofs/lib/libgcc_s.so.1
b75bd000-b7d40000 rw-p b75bd000 00:00 0 
b7d40000-b7d43000 r-xp 00000000 07:00 103771     /rofs/lib/libuuid.so.1.2
b7d43000-b7d44000 rw-p 00002000 07:00 103771     /rofs/lib/libuuid.so.1.2
b7d44000-b7d46000 r-xp 00000000 07:00 103855     /rofs/lib/tls/i686/cmov/libdl-2.7.so
b7d46000-b7d48000 rw-p 00001000 07:00 103855     /rofs/lib/tls/i686/cmov/libdl-2.7.so
b7d48000-b7d49000 rw-p b7d48000 00:00 0 
b7d49000-b7e92000 r-xp 00000000 07:00 103852     /rofs/lib/tls/i686/cmov/libc-2.7.so
b7e92000-b7e93000 r--p 00149000 07:00 103852     /rofs/lib/tls/i686/cmov/libc-2.7.so
b7e93000-b7e95000 rw-p 0014a000 07:00 103852     /rofs/lib/tls/i686/cmov/libc-2.7.so
b7e95000-b7e98000 rw-p b7e95000 00:00 0 
b7e98000-b7ef6000 r-xp 00000000 07:00 106327     /rofs/lib/libparted-1.7.so.1.0.0
b7ef6000-b7ef8000 rw-p 0005d000 07:00 106327     /rofs/lib/libparted-1.7.so.1.0.0
b7ef8000-b7ef9000 rw-p b7ef8000 00:00 0 
b7f02000-b7f06000 rw-p b7f02000 00:00 0 
b7f06000-b7f07000 r-xp b7f06000 00:00 0          [vdso]
b7f07000-b7f21000 r-xp 00000000 07:00 103665     /rofs/lib/ld-2.7.so
b7f21000-b7f23000 rw-p 00019000 07:00 103665     /rofs/lib/ld-2.7.so
bfbf0000-bfc05000 rw-p bffeb000 00:00 0          [stack]
[/I]

---

### Post by jimv on 2008-07-20
You could try installing with the alternate CD.  That's a CD that just goes straight to the install without loading up an X session.

If you go to the Ubuntu download page, you'll see a checkbox for Alternate CD near the bottom.

---

### Post by speculatius on 2008-07-20
There was some problem on disk. I deleted all partitions and started from scratch. And ubuntu is going well now :)

Thanks...

---

