---
title: "Authentication problem using winbind"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by Piviul on 2014-05-08
I've just upgraded a netbook from ubuntu 12.04 to 14.04. All seems to works except that remote users can't logon anymore. Remote users are users from a samba3 domain. Logon is successful from console but not from lightdm. This is the output of /var/log/lightdm/lightdm.log:

[+2952.11s] DEBUG: Session pid=12877: Continue authentication
[+2955.12s] DEBUG: Session pid=12946: Authentication complete with return value 0: Success
[+2955.12s] DEBUG: Session pid=12877: Authenticate result for user DOMINIOCSA\psala: Success
[+2955.12s] DEBUG: Session pid=12877: User DOMINIOCSA\psala authorized
[+2955.13s] DEBUG: Session pid=12877: Greeter requests default session
[+2955.13s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+2955.13s] DEBUG: Session pid=12877: Sending SIGTERM
[+2955.17s] DEBUG: Session pid=12877: Exited with return value 0
[+2955.17s] DEBUG: Seat: Session stopped
[+2955.17s] DEBUG: Seat: Greeter stopped, running session
[+2955.17s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session8
[+2955.17s] DEBUG: Session pid=12946: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+2955.18s] DEBUG: Creating shared data directory /var/lib/lightdm-data/DOMINIOCSA\psala
[+2955.18s] DEBUG: Session pid=12946: Logging to .xsession-errors
[+2955.28s] DEBUG: Activating VT 7
[+2955.28s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c22
[+2956.69s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+2959.86s] DEBUG: Session pid=12946: Exited with return value 0
[+2959.86s] DEBUG: Seat: Session stopped
[+2959.86s] DEBUG: Seat: Stopping display server, no sessions require it
[+2959.86s] DEBUG: Sending signal 15 to process 12872
[+2960.50s] DEBUG: Process 12872 exited with return value 0
[+2960.50s] DEBUG: DisplayServer x-0: X server stopped
[+2960.50s] DEBUG: Releasing VT 7
[+2960.50s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+2960.50s] DEBUG: Seat: Display server stopped
[+2960.50s] DEBUG: Seat: Active display server stopped, starting greeter
[+2960.50s] DEBUG: Seat: Creating greeter session
[+2960.50s] DEBUG: Seat: Creating display server of type x
[+2960.50s] DEBUG: Using VT 7
[+2960.50s] DEBUG: Seat: Starting local X display on VT 7
[+2960.50s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+2960.50s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+2960.50s] DEBUG: DisplayServer x-0: Launching X Server
[+2960.50s] DEBUG: Launching process 13551: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+2960.50s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+2960.79s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+2960.90s] DEBUG: Got signal 10 from process 13551
[+2960.90s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+2960.90s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+2960.90s] DEBUG: Seat: Display server ready, starting session authentication
[+2960.90s] DEBUG: Session pid=13561: Started with service 'lightdm-greeter', username 'lightdm'
[+2961.04s] DEBUG: Session pid=13561: Authentication complete with return value 0: Success
[+2961.04s] DEBUG: Seat: Session authenticated, running command
[+2961.04s] DEBUG: Session pid=13561: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+2961.04s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+2961.04s] DEBUG: Session pid=13561: Logging to /var/log/lightdm/x-0-greeter.log
[+2961.10s] DEBUG: Activating VT 7
[+2961.10s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c23
[+2961.54s] DEBUG: Session pid=13561: Greeter connected version=1.10.0
[+2962.01s] DEBUG: Session pid=13561: Greeter start authentication
[+2962.01s] DEBUG: Session pid=13628: Started with service 'lightdm', username '(null)'
[+2962.03s] DEBUG: Session pid=13628: Got 1 message(s) from PAM
[+2962.03s] DEBUG: Session pid=13561: Prompt greeter with 1 message(s)

Can you please suggest me a solution?

Piviul

---

### Post by Piviul on 2014-05-08
After a restart all seems to be solved.

Thanks a lot

Piviul

---

