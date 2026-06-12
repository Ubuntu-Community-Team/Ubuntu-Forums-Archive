---
title: "Stand by and Title Bars"
date: 2009-08-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zoomy942 on 2009-08-28
Can anyone confirm that once you go into stand by or hibernate, and wake your PC, the title vars are gone?

Maybe its a new intel bug?  It was working until the updates 2 days ago.

---

### Post by zoomy942 on 2009-08-28
Anyone?  Bueller?

---

### Post by taavikko on 2009-08-28
> **zoomy942 said:**
> Anyone?  Bueller?

Ferris has a day off ;)

after suspend metacity works correctly here.
Can't test compiz since not capable GPU (yet)

ps. please don't bump posts in such a short time.

---

### Post by Tibuda on 2009-08-28
Works fine here.

---

### Post by 23meg on 2009-08-28
I have the same issue, with Compiz only.

---

### Post by cdEWoozy on 2009-08-28
Same here, also running compiz. I couldn't find any error messages in .xsession-errors, strange. Restarting compiz restored the window decorations.

---

### Post by zoomy942 on 2009-08-28
I will file a bug if no one else has.

---

### Post by Eddie Hung on 2009-08-29
Go ahead: I can confirm this too. As far as I know, only started happening recently (I wasn't able to really suspend until now, on 2.6.31.8).

Intel C2D (AMD64) on Intel DG45FC with X4500HD here.

I couldn't see any indication that compiz had crashed in dmesg; but I did spot this every time I resume, though it might not be related (I found one bug report about it here: [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/418417](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/418417))
EDIT: There seems to be quite a few related to this check_for_bios_corruption: [https://bugs.launchpad.net/ubuntu/+source/linux?field.searchtext=check_for_bios_corruption&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+source/linux?field.searchtext=check_for_bios_corruption&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=) but no mention of this symptom, so likely unrelated...

```
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816047] ------------[ cut here ]------------
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816053] WARNING: at /build/buildd/linux-2.6.31/arch/x86/kernel/check.c:134 check_for_bios_corruption+0xe5/0x100()
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816055] Hardware name:         
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816057] Modules linked in: ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs exportfs reiserfs nls_iso8859_1 nls_cp437 vfat fat binfmt_misc coretemp lp parport snd_hda_codec_intelhdmi snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event psmouse snd_seq serio_raw snd_timer snd_seq_device heci(C) snd soundcore snd_page_alloc joydev hid_logitech ff_memless usb_storage e1000e usbhid dm_raid45 xor fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit video output intel_agp
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816095] Pid: 9, comm: events/0 Tainted: G         C 2.6.31-8-generic #28-Ubuntu
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816097] Call Trace:
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816102]  [<ffffffff81059738>] warn_slowpath_common+0x78/0xb0
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816105]  [<ffffffff810597cc>] warn_slowpath_fmt+0x3c/0x40
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816108]  [<ffffffff810326c5>] check_for_bios_corruption+0xe5/0x100
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816111]  [<ffffffff810326e0>] ? check_corruption+0x0/0x30
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816114]  [<ffffffff810326e9>] check_corruption+0x9/0x30
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816118]  [<ffffffff8106e7c5>] run_workqueue+0x95/0x170
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816120]  [<ffffffff8106e944>] worker_thread+0xa4/0x120
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816124]  [<ffffffff81073b50>] ? autoremove_wake_function+0x0/0x40
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816127]  [<ffffffff8106e8a0>] ? worker_thread+0x0/0x120
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816129]  [<ffffffff81073766>] kthread+0xa6/0xb0
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816132]  [<ffffffff8101308a>] child_rip+0xa/0x20
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816135]  [<ffffffff810736c0>] ? kthread+0x0/0xb0
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816137]  [<ffffffff81013080>] ? child_rip+0x0/0x20
Aug 29 00:23:28 eddies-desktop kernel: [ 3360.816139] ---[ end trace e5af0227a1585c98 ]---

```

Eddie

---

### Post by berthiggins on 2009-08-29
Yes my bars dissapear too a compiz restart brings them back.

---

### Post by woedend on 2009-08-29
Same problem here...very annoying!  Have you filed a bug report yet sir?
Does anyone know offhand where to edit the config for the hibernate/resume function so that I can have it autoreload the window decorator upon resuming?

---

### Post by zoomy942 on 2009-08-29
I haven't yet because I haven't figured out what to post as a bug. Not sure where it would be in an error log. 

What say you fellas?

---

### Post by zoomy942 on 2009-08-31
bug filed

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/421900]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/421900")

---

