---
title: "ASUS M4A785D-M no picture"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by dava4444 on 2011-03-27
Hi

I have a bit of a problem...

I have a ASUS M4A785D-M mobo, and have installed win7, I want to use the comp for a DAW with Ubuntu via downloading the Studio packages after install, but neither the live disc or wubi will show a picture on my TV, HDMI or DVI, no picture...?!!??

my TV does all res. upto 1080p. I have had Ubuntu on this TV before, but this time i'm a bit stuck... I also read to press f6 and put 'nomodeset', but if that doesn't work, i'll need some help, like how do i get the ingfx working via hdmi?  i'll be back...

I sometimes get this error also:


'03-27 04:41 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ebfd7f8f-51ca-11e0-872e-ad25a023d86e} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ebfd7f8f-51ca-11e0-872e-ad25a023d86e} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
03-27 04:41 DEBUG  TaskList: # Cancelling tasklist
03-27 04:41 DEBUG  TaskList: New task modify_bcd
03-27 04:41 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ebfd7f8f-51ca-11e0-872e-ad25a023d86e} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {ebfd7f8f-51ca-11e0-872e-ad25a023d86e} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
03-27 04:41 DEBUG  TaskList: New task modify_bcd
03-27 04:41 DEBUG  TaskList: ## Finished modify_bootloader
03-27 04:41 DEBUG  TaskList: # Finished tasklist'

please help

I don't get it on the C:/ drive though.

I'm useing 64 bit win7 prem.

thanks

Dava

---

### Post by dava4444 on 2011-03-27
nup still can't get anything going,

and now the partition i was going to use is not showing up on the alt CD, very odd.

ahh wellll.

:(

Dava

---

