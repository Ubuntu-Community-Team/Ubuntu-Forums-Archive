---
title: "Upgraded to 16.04, 100% CPU usage when watching videos"
date: 2016-06-29
forum: Installation &amp; Upgrades
---

### Post by john568 on 2016-06-29
I was running Ubuntu 14 with zero issues. After the upgrade my CPU periodically hits 100% when watching videos or doing graphical things. Netflix, local videos, graphical HTML5 programming, etc. Oddly, when I open the system monitor the CPU drops making it difficult to diagnose the problem. I usually see Chrome using ~14% CPU and everything else at 0%. The local video player uses ~4% CPU, same situation. If I pause the video for a while the CPU drops back to normal.

System details:
Ubuntu 16.04 LTS
Memory: 7.7 GiB
Processor: Intel® Core™ i7-3520M CPU @ 2.90GHz × 4 
Graphics: Gallium 0.4 on AMD TURKS (DRM 2.43.0, LLVM 3.8.0) (Different from when I was using Ubuntu 14 I think?)
OS Type: 64-bit
Disk: 483.7 GB

---

### Post by mastablasta on 2016-06-29
the GPU chip used proprietary drivers before but they are no longer available for it. it could be that current radeon drivers do not support  you chip well. they are 20%-30% worse then fglrx. however the CPU should not be used as they seem to be up and running.

i suggest you install 14.04 for now (supported until 2019), if it worked better.

to monitor CPU usage you can use top or htop command in terminal.

---

### Post by john568 on 2016-06-30
I got a cooling fan for the laptop and it seems to have fixed all issues. Very odd. I'm guessing the GPU was getting too hot and the drivers decided to offload the work to the CPU? That would explain the erratic rising/falling of the CPU. Stress testing by running Netflix and HTML5 canvas animations simultaneously now barely makes a dent in the CPU usage.

---

