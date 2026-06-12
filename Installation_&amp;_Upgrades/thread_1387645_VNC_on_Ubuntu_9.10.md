---
title: "VNC on Ubuntu 9.10"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by auraithx on 2010-01-22
I'm trying to set-up VNC on my linode server so that I can access it via VNC from work, after trials and tribulations I think I've got it setup right.

```
root@hostname:~# sudo netstat -tap | grep xinetd
tcp        0      0 *:5901                  *:*                     LISTEN      7047/xinetd
root@hostname:~# vncserver

New 'hostname:5 (root)' desktop is hostname:5

Starting applications specified in /root/.vnc/xstartup
Log file is /root/.vnc/hostname:5.log

root@hostname:~# vncviewer localhost:1
Error: Can't open display:

```

I figure the last error is because I'm accessing my server via SSH? 

However, when I open up VNC viewer on windows and try to connect I get a 'Connection Refused' error

---

### Post by auraithx on 2010-01-22
second page already?

---

### Post by pricetech on 2010-01-22
VNC is not a good choice because of security concerns.  You can tunnel it over SSH for security, but there are (in my opinion) better solutions.

Install NX from nomachine.com.  Client, Node, Server for Linux and Client for winders.

Works like a charm.

---

### Post by auraithx on 2010-01-25
Okay, firstly I couldn't install because of a common bug. So I followed the instructions posted here by 
[sperlyjinx's ]("http://ubuntuforums.org/showthread.php?t=784880#3") 


Now - I can see the machine, and it accepts my password but I'm still getting a error message

```

NX> 148 Server capacity: not reached for user: username
NX> 105 Start session with: --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="linode" --type="unix-kde" --geometry="1146x802" --client="winnt" --keyboard="pc102\057gb" --screeninfo="1146x802x32+render" 
NXSERVER - Version 3.4.0-8 - LFE
Mon Jan 25 09:56:16 2010 running as user: 'nx' (uid: 105, pid: 15863) on 'hostname'
Info: user login is username(NXShell)
Info: user password is '******' (NXShell)
Info: using 'sshd authentication' (NXShell)
Info: selected user 'username' is authenticated (NXNodeExec)
Info: password for selected user is in 'text' mode (NXNodeExec)
Info: preferred auth method is '' (NXNodeExec)
Info: selected NX Node with host name 'localhost', port '22' (NXNodeExec)
Info: selected publickey method to login NX Node (NXNodeExec)
Info: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l username localhost -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec)
Info: nxssh child pid is: 15884 (NXNodeExec)
Info: received data in out channel from NX Node: 'NX> 204 Authentication failed.
' (NXNodeExec)
Error: received message 'Authentication Failure' from nxssh (NXNodeExec)
Info: closing nxssh's in, out, err FDs (flagfinished is: 1) (NXNodeExec)
Error: failed to authenticate on NX Node (NXNodeExec)
Info: trying next authentication method. (NXNodeExec)
Info: selected NX Node with host name 'localhost', port '22' (NXNodeExec)
Info: selected password method to login NX Node (NXNodeExec)
Info: now retrying to authenticate with 'password' on NX Node (NXNodeExec)
Info: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l username localhost -p 22 -x -2 -o 'PasswordAuthentication yes' -o 'PubkeyAuthentication no' -o 'RhostsAuthentication no' -o 'RSAAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec)
Info: nxssh child pid is: 15888 (NXNodeExec)
Info: received data in out channel from NX Node: 'NX> 205 username@localhost's password: ' (NXNodeExec)
Info: received request for password from nxssh, user password sent (NXNodeExec)
Info: received data in out channel from NX Node: '
' (NXNodeExec)
Info: Removing not recognized buffer from stdout:[
] (NXNodeExec)
Info: received data in err channel from NX Node: 'NX> 595 ERROR: Initialization failed: Can't open file: /usr/NX/etc/node.cfg.
NX> 595 ERROR: No such file or directory. Please try to fix the problem by
NX> 595 ERROR: running /usr/NX/scripts/setup/nxnode --install.
' (NXNodeExec)
Info: NX Node out channel was closed (NXNodeExec)
Info: NX Node err channel was closed (NXNodeExec)
Info: closing nxssh's in, out, err FDs (flagfinished is: 0) (NXNodeExec)
Error: no 'CONNECTED' message from NX Node (NXNodeExec)
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 7DD9D5ED. To get detailed information about
NX> 595 ERROR: the error search for the string 7DD9D5ED in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15


```

Here's my var/log/messages output

```
Jan 25 10:19:21 hostname NXSERVER-3.4.0-8[15935]: User 'username' logged in from '217.36.209.41'. 'NXLogin::set'
Jan 25 10:19:23 hostname NXSERVER-3.4.0-8[15935]: Selected node host:localhost with port:22 'main::selectNode'
Jan 25 10:19:23 hostname NXSERVER-3.4.0-8[15935]: Current selected node: localhost is in status: running  'main::selectNode'
Jan 25 10:19:23 hostname NXSERVER-3.4.0-8[15935]: Selected session type: unix-kde allowed in the profile of user: username'NXShell::Static'
Jan 25 10:19:23 hostname NXSERVER-3.4.0-8[15935]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Jan 25 10:19:24 hostname NXNODE-3.4.0-6[15971]: ERROR: Initialization fail: can't open file '/usr/NX/etc/node.cfg: No such file or directory Logger::log nxnode 658
Jan 25 10:19:24 hostname NXNODE-3.4.0-6[15971]: ERROR: No such file or directory. Please try to fix the problem by Logger::log nxnode 659
Jan 25 10:19:24 hostname NXNODE-3.4.0-6[15971]: ERROR: running: /usr/NX/scripts/setup/nxserver --install Logger::log nxnode 660
Jan 25 10:19:26 hostname NXSERVER-3.4.0-8[15935]: ERROR: nxssh process exited with '1' 'NXNodeExec::exec'
Jan 25 10:19:26 hostname NXSERVER-3.4.0-8[15935]: ERROR: (exception id 4A7D3817) Error: no 'CONNECTED' message from NX Node
Jan 25 10:19:26 hostname NXSERVER-3.4.0-8[15935]: ERROR: (exception id 4A7D3817) NX> 595 ERROR: Initialization failed: Can't open file: /usr/NX/etc/node.cfg.
Jan 25 10:19:26 hostname NXSERVER-3.4.0-8[15935]: ERROR: (exception id 4A7D3817) NX> 595 ERROR: No such file or directory. Please try to fix the problem by
Jan 25 10:19:26 hostname NXSERVER-3.4.0-8[15935]: ERROR: (exception id 4A7D3817) NX> 595 ERROR: running /usr/NX/scripts/setup/nxnode --install.
Jan 25 10:19:26 hostname NXSERVER-3.4.0-8[15935]: ERROR: (exception id 4A7D3817) NXNodeExec::exec('startsession', 'user=username&userip=**&uniqueid=76D7CC90A1AE23...', 'localhost', 22) called at handlers/nxserver.pl line 3575
Jan 25 10:19:26 hostname NXSERVER-3.4.0-8[15935]: ERROR: (exception id 4A7D3817) NXShell::handler_session_start('--link="adsl" --backingstore="1" --encryption="1" --cache="16M" ...') called at NXShell.pm line 373
Jan 25 10:19:26 hostname NXSERVER-3.4.0-8[15935]: ERROR: (exception id 4A7D3817) NXShell::handle_command('startsession', '--link="adsl" --backingstore="1" --encryption="1" --cache="16M" ...') called at NXShell.pm line 145
Jan 25 10:19:26 hostname NXSERVER-3.4.0-8[15935]: ERROR: (exception id 4A7D3817) NXShell::run() called at nxserver.pl line 4493
Jan 25 10:19:26 hostname NXSERVER-3.4.0-8[15935]: ERROR: (exception id 4A7D3817) eval {...} called at nxserver.pl line 4452
```

---

### Post by auraithx on 2010-01-25
update. I tried running those commands it gave me in the error log. Didn't work so I installed CUPS by using
```
aptitude install cupsys cupsys-client
```. I now get the following errors

NX Output
```
NX> 203 NXSSH running with pid: 3368
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 109.74.204.14 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.4.0-8 - LFE
NX> 105 Hello NXCLIENT - Version 3.4.0
NX> 134 Accepted protocol: 3.4.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: mglasgow
NX> 102 Password: **********
NX> 103 Welcome to: CravenPublishing user: mglasgow
NX> 105 Listsession --user="mglasgow" --status="suspended\054running" --geometry="1152x864x32+render" --type="unix-kde" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: mglasgow
NX> 105 Start session with: --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="linode" --type="unix-kde" --geometry="1146x802" --client="winnt" --keyboard="pc102\057gb" --screeninfo="1146x802x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: FB613B8A. To get detailed information about
NX> 595 ERROR: the error search for the string FB613B8A in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15
```

/var/log/messages
```
Jan 25 10:29:26 hostname NXSERVER-3.4.0-8[17913]: User 'username' logged in from '217.36.209.41'. 'NXLogin::set'
Jan 25 10:29:28 hostname NXSERVER-3.4.0-8[17913]: Selected node host:localhost with port:22 'main::selectNode'
Jan 25 10:29:28 hostname NXSERVER-3.4.0-8[17913]: Current selected node: localhost is in status: running  'main::selectNode'
Jan 25 10:29:28 hostname NXSERVER-3.4.0-8[17913]: Selected session type: unix-kde allowed in the profile of user: username 'NXShell::Static'
Jan 25 10:29:30 hostname NXSERVER-3.4.0-8[17913]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Jan 25 10:29:31 hostname NXSERVER-3.4.0-8[17913]: A valid NX Server public SSH key is missing on the node. '(eval)'
Jan 25 10:29:33 hostname NXNODE-3.4.0-6[17951]: ERROR: NX> 596 ERROR: NXNODE Ver. 3.4.0-6  (Error id eCB9E68) [eCB9E68] Logger::log nxnode 2956
Jan 25 10:29:33 hostname NXNODE-3.4.0-6[17951]: ERROR: NX> 596 ERROR: create session: run commands [eCB9E68] Logger::log nxnode 2956
Jan 25 10:29:33 hostname NXNODE-3.4.0-6[17951]: ERROR: NX> 596 ERROR: execution of last command failed [eCB9E68] Logger::log nxnode 2956
Jan 25 10:29:33 hostname NXNODE-3.4.0-6[17951]: ERROR: NX> 596 last command: /bin/mkdir -p /home/username/.nx/C-hostname-1004-9F3142F7734AA76EE8E83B02E028F239 [eCB9E68] Logger::log nxnode 2956
Jan 25 10:29:33 hostname NXNODE-3.4.0-6[17951]: ERROR: NX> 596 exit value: 1 [eCB9E68] Logger::log nxnode 2956
Jan 25 10:29:33 hostname NXNODE-3.4.0-6[17951]: ERROR: NX> 596 stdout:  [eCB9E68] Logger::log nxnode 2956
Jan 25 10:29:33 hostname NXNODE-3.4.0-6[17951]: ERROR: NX> 596 stderr: /bin/mkdir: cannot create directory `/home/username/.nx': Permission denied [eCB9E68] Logger::log nxnode 2956
Jan 25 10:29:33 hostname NXNODE-3.4.0-6[17951]: ERROR: NX> 596 . [eCB9E68] Logger::log nxnode 2956
Jan 25 10:29:33 hostname NXNODE-3.4.0-6[17951]: ERROR: NX> 596 init: stdin arguments: user=username,userip=217%2e36%2e209%2e41,uniqueid=9F3142F7734AA76EE8E83B02E028F239,display=1004,node_number=0,server_name=hostname,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=109%2e74%2e204%2e14,encryption_mode=3,connection=local,images=64M,cache=16M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=linode,shmem=1,type=unix%2dkde,virtualdesktop=1,screeninfo=1146x802x32%2brender,keyboard=pc102%2fgb,geometry=1146x802,link=adsl Logger::log nxnode 2956
Jan 25 10:29:34 hostname NXSERVER-3.4.0-8[17913]: ERROR: (exception id FB613B8A) NX> 596 ERROR: NXNODE Ver. 3.4.0-6  (Error id eCB9E68)
Jan 25 10:29:34 hostname NXSERVER-3.4.0-8[17913]: ERROR: (exception id FB613B8A) NX> 596 ERROR: create session: run commands
Jan 25 10:29:34 hostname NXSERVER-3.4.0-8[17913]: ERROR: (exception id FB613B8A) NX> 596 ERROR: execution of last command failed
Jan 25 10:29:34 hostname NXSERVER-3.4.0-8[17913]: ERROR: (exception id FB613B8A) NX> 596 last command: /bin/mkdir -p /home/username/.nx/C-hostname-1004-9F3142F7734AA76EE8E83B02E028F239
Jan 25 10:29:34 hostname NXSERVER-3.4.0-8[17913]: ERROR: (exception id FB613B8A) NX> 596 exit value: 1
Jan 25 10:29:34 hostname NXSERVER-3.4.0-8[17913]: ERROR: (exception id FB613B8A) NX> 596 stdout: 
Jan 25 10:29:34 hostname NXSERVER-3.4.0-8[17913]: ERROR: (exception id FB613B8A) NX> 596 stderr: /bin/mkdir: cannot create directory `/home/username/.nx': Permission denied
Jan 25 10:29:34 hostname NXSERVER-3.4.0-8[17913]: ERROR: (exception id FB613B8A) NX> 596 init: stdin arguments: user=username,userip=217%2e36%2e209%2e41,uniqueid=9F3142F7734AA76EE8E83B02E028F239,display=1004,node_number=0,server_name=hostname,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=109%2e74%2e204%2e14,encryption_mode=3,connection=local,images=64M,cache=16M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=linode,shmem=1,type=unix%2dkde,virtualdesktop=1,screeninfo=1146x802x32%2brender,keyboard=pc102%2fgb,geometry=1146x802,link=adsl
Jan 25 10:29:34 hostname NXSERVER-3.4.0-8[17913]: ERROR: (exception id FB613B8A) NXNodeExec::exec('startsession', 'user=username&userip=217%2e36%2e209%2e41&uniqueid=9F3142F7734AA7...', 'localhost', 22) called at handlers/nxserver.pl line 3575
Jan 25 10:29:34 hostname NXSERVER-3.4.0-8[17913]: ERROR: (exception id FB613B8A) NXShell::handler_session_start('--link="adsl" --backingstore="1" --encryption="1" --cache="16M" ...') called at NXShell.pm line 373
Jan 25 10:29:34 hostname NXSERVER-3.4.0-8[17913]: ERROR: (exception id FB613B8A) NXShell::handle_command('startsession', '--link="adsl" --backingstore="1" --encryption="1" --cache="16M" ...') called at NXShell.pm line 145
Jan 25 10:29:34 hostname NXSERVER-3.4.0-8[17913]: ERROR: (exception id FB613B8A) NXShell::run() called at nxserver.pl line 4493
Jan 25 10:29:34 hostname NXSERVER-3.4.0-8[17913]: ERROR: (exception id FB613B8A) eval {...} called at nxserver.pl line 4452
```

**update 3**
Fixed above by using
```
chmod -R -f 0777 /home/username
```

am now getting the following erros (it logs in and shows me a black screen)

```
Xsession: unable to launch "startkde" X session --- "startkde" not found; 
falling back to default session
```

```
Xsession: unable to start X session --- no "/home/username/.xsession" file, no 
"/home/username/.Xsession" file, no session managers, no window managers, and 
no terminal emulators found; aborting.
```

---

### Post by lame_steed on 2010-01-26
It looks like startkde excutable file is not installed to your system.

> apt-get install kdebase-workspace-bin 
should resolve you issue (startkde is a part of this package)

---

