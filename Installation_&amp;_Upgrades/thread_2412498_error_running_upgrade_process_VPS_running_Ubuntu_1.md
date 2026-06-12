---
title: "error running upgrade process VPS running Ubuntu 16.04"
date: 2019-02-13
forum: Installation &amp; Upgrades
---

### Post by aahepp2 on 2019-02-13
did my normal sudo apt update and upgrade.  The upgrade try doing an upgrade on ssh which threw the following message:

Setting up openssh-server (1:7.2p2-4ubuntu2.7) ...
Failed to validate path /var/run/sshd: Too many levels of symbolic links
insserv: warning: script 'vps-server' missing LSB tags and overrides
Job for ssh.service failed because the control process exited with error code. See "systemctl status ssh.service" and "journalctl -xe" for details.
invoke-rc.d: initscript ssh, action "restart" failed.
â ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2019-02-13 21:28:15 UTC; 47ms ago
  Process: 5440 ExecStart=/usr/sbin/sshd -D $SSHD_OPTS (code=exited, status=255)
  Process: 5437 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
 Main PID: 5440 (code=exited, status=255)

Feb 13 21:28:15 vps-server systemd[1]: Starting OpenBSD Secure Shell server...
Feb 13 21:28:15 vps-server sshd[5440]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Feb 13 21:28:15 vps-server systemd[1]: ssh.service: Main process exited, code=exited, status=255/n/a
Feb 13 21:28:16 vps-server systemd[1]: Failed to start OpenBSD Secure Shell server.
Feb 13 21:28:16 vps-server systemd[1]: ssh.service: Unit entered failed state.
Feb 13 21:28:16 vps-server systemd[1]: ssh.service: Failed with result 'exit-code'.
dpkg: error processing package openssh-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 openssh-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

Only way into the machine is via ssh.  Server still functions as normal, but keep getting that error message every time I run an update function.  1st time encountering this issue.

---

