---
title: "Chrome + Firefox problems after upgrade 22.10 &gt; 23.04"
date: 2023-04-22
forum: Installation &amp; Upgrades
---

### Post by wern1 on 2023-04-22
After upgrading to 23.04 both Firefox and Chrome show problems. On both items on the "Menu" bar are not clickable any more. 
After deleting Chrome and reinstalling it, Chrome cannot be opened any more at all.

in Terminal windows: $ google-chrome-stable:  shows the following error message: *** stack smashing detected ***: terminated

I have not reinstalled firefox yet as it is usable, except the clicking on menu-bar items does not work

Anybody also experiencing problems??

**Problem "kind of" solved:**
I switched to Xorg, reinstalled chrome, deleted various files with "autoremove" and both Firfox and Chrome worked with Xorg
Then I switched back to Wayland and now both Firefox and Chrome are also working in Wayland. 
Totally lost as to why!

---

### Post by arekm2 on 2023-06-04
Same here. With --no-sanbox it works but that sucks. Didn't find a proper solution for the problem.
~$ google-chrome
*** stack smashing detected ***: terminated
[4201:4201:0604/131915.782781:ERROR:gpu_process_host.cc(953)] GPU process exited unexpectedly: exit_code=134
*** stack smashing detected ***: terminated
[4201:4201:0604/131916.125662:ERROR:gpu_process_host.cc(953)] GPU process exited unexpectedly: exit_code=134
*** stack smashing detected ***: terminated
[4201:4201:0604/131916.431475:ERROR:gpu_process_host.cc(953)] GPU process exited unexpectedly: exit_code=134
*** stack smashing detected ***: terminated
[4201:4201:0604/131916.639780:ERROR:gpu_process_host.cc(953)] GPU process exited unexpectedly: exit_code=134
*** stack smashing detected ***: terminated
[4201:4201:0604/131916.828553:ERROR:gpu_process_host.cc(953)] GPU process exited unexpectedly: exit_code=134
*** stack smashing detected ***: terminated
[4201:4201:0604/131917.001080:ERROR:gpu_process_host.cc(953)] GPU process exited unexpectedly: exit_code=134
*** stack smashing detected ***: terminated
[4201:4201:0604/131917.279378:ERROR:gpu_process_host.cc(953)] GPU process exited unexpectedly: exit_code=134
*** stack smashing detected ***: terminated
[4201:4201:0604/131917.467152:ERROR:gpu_process_host.cc(953)] GPU process exited unexpectedly: exit_code=134
*** stack smashing detected ***: terminated
[4201:4201:0604/131917.648105:ERROR:gpu_process_host.cc(953)] GPU process exited unexpectedly: exit_code=134
[4201:4201:0604/131917.648124:FATAL:gpu_data_manager_impl_private.cc(431)] GPU process isn't usable. Goodbye.
[0604/131917.656570:ERROR:elf_dynamic_array_reader.h(64)] tag not found
Trace/breakpoint trap (core dumped)

Edit: --disable-seccomp-filter-sandbox is enough

---

