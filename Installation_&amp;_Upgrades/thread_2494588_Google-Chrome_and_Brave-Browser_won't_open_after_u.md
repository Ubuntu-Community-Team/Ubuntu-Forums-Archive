---
title: "Google-Chrome and Brave-Browser won't open after upgrade"
date: 2024-01-20
forum: Installation &amp; Upgrades
---

### Post by dbjerke00 on 2024-01-20
Yesterday I happened to notice that my brave-browser had the update notification in the top right so I clicked on it and restarted it.  It immediately crashed.  Same results after a reboot so I did an apt upgrade and then another reboot and google-chrome also started crashing on start.  I was able to install an older version of brave-browser (from 1.61.120 to version 1.58.137) and that started working again.  I have not tried to install an older version of google-chrome yet.

When I try to start google-chrome on the cli I get:
$ google-chrome-stable 
MESA-INTEL: warning: Haswell Vulkan support is incomplete
[63287:63287:0120/121012.253522:ERROR:gpu_process_host.cc(992)] GPU process exited unexpectedly: exit_code=133
MESA-INTEL: warning: Haswell Vulkan support is incomplete
[63287:63287:0120/121012.590307:ERROR:gpu_process_host.cc(992)] GPU process exited unexpectedly: exit_code=133
MESA-INTEL: warning: Haswell Vulkan support is incomplete
[63287:63287:0120/121012.818344:ERROR:gpu_process_host.cc(992)] GPU process exited unexpectedly: exit_code=133
MESA-INTEL: warning: Haswell Vulkan support is incomplete
[63287:63287:0120/121013.006791:ERROR:gpu_process_host.cc(992)] GPU process exited unexpectedly: exit_code=133
MESA-INTEL: warning: Haswell Vulkan support is incomplete
[63287:63287:0120/121013.186258:ERROR:gpu_process_host.cc(992)] GPU process exited unexpectedly: exit_code=133
MESA-INTEL: warning: Haswell Vulkan support is incomplete
[63287:63287:0120/121013.367125:ERROR:gpu_process_host.cc(992)] GPU process exited unexpectedly: exit_code=133
[63287:63287:0120/121013.536401:ERROR:gpu_process_host.cc(992)] GPU process exited unexpectedly: exit_code=133
[63287:63287:0120/121013.691732:ERROR:gpu_process_host.cc(992)] GPU process exited unexpectedly: exit_code=133
[63287:63287:0120/121013.842820:ERROR:gpu_process_host.cc(992)] GPU process exited unexpectedly: exit_code=133
[63287:63287:0120/121013.842836:FATAL:gpu_data_manager_impl_private.cc(448)] GPU process isn't usable. Goodbye.
Trace/breakpoint trap (core dumped)


My GPU in is just the Intel CPU - no stand alone GPU.

$ sudo apt list mesa-*-drivers --installed
Listing... Done
mesa-va-drivers/focal,now 22.2.0.20220625.1+3091 amd64 [installed,automatic]
mesa-vdpau-drivers/focal,now 22.2.0.20220625.1+3091 amd64 [installed,automatic]
mesa-vulkan-drivers/focal,now 22.2.0.20220625.1+3091 amd64 [installed,automatic]


Looking to see if anyone has any suggestions.  I'm running Ubuntu 20.04.6

---

### Post by dbjerke00 on 2024-01-26
Has anyone else had this issue?  Not sure what to try but right now I'm having to run old versions of the browsers to be able to get on the web.  It was fine before the ubuntu upgrade.

---

### Post by SeijiSensei on 2024-01-26
Maybe take a look at this?

[https://www.google.com/search?client=firefox-b-1-d&q=MESA-INTEL%3A+warning%3A+Haswell+Vulkan+support+is+incomplete](https://www.google.com/search?client=firefox-b-1-d&q=MESA-INTEL%3A+warning%3A+Haswell+Vulkan+support+is+incomplete)

---

### Post by dbjerke00 on 2024-01-29
I finally figured out that if I disable accelerated video decoding that it allows it to startup.

google-chrome-stable --disable-accelerated-video-decode

Once I had it open I disabled it in the settings so it will load without having to use the CLI.  My Brave browser is still on the older code.

I don't understand why I suddenly had to change this after an upgrade but clearly something changed that is global to both chrome and brave.

---

