---
title: "Wine Error"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by dimas869 on 2012-02-02
i am trying to run a .exe application and this is what i get so could someone help me fix it please
> fixme:gstreamer:event_sink 0x7d8c5518 stub tag
fixme:gstreamer:got_data_sink Triggering 0x7d8da008 0xc0
fixme:gstreamer:watch_bus mpegaudioparse0: GStreamer encountered a general stream error.
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:gstreamer:GST_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:DSoundRender_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
err:ntdll:RtlpWaitForCriticalSection section 0x1129d98 "gstdemux.c: GSTImpl.csFilter" wait timed out in thread 002c, blocked by 0009, retrying (60 sec)
wine: Critical section 01129d98 wait failed at address 0x7bc3489a (thread 002c), starting debugger...
Unhandled exception: wait failed on critical section 0x01129d98 in 32-bit code (0x7bc3489a).
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc3489a
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process tid prio (all id:s are in hex)
[email]ramon@miputacomputadora:~/.wine[/email]/drive_c/Programs/AirAttack$ 0000000e services.exe
0000001e 0
0000001d 0
00000015 0
00000010 0
0000000f 0
00000012 winedevice.exe
00000020 0
00000019 0
00000014 0
00000013 0
0000001a plugplay.exe
0000001f 0
0000001c 0
0000001b 0
00000021 explorer.exe
00000022 0
winedbg: Internal crash at 0x6837f29a
err:ntdll:RtlDeleteResource Deleting active MRSW lock (0x11249c), expect failure
err:ntdll:RtlDeleteResource Deleting active MRSW lock (0x111f64), expect failure


---

