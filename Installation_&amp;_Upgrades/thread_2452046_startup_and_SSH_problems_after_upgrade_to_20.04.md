---
title: "startup and SSH problems after upgrade to 20.04"
date: 2020-10-15
forum: Installation &amp; Upgrades
---

### Post by alfred-holzherr on 2020-10-15
Hello dear community,

I upgraded from Ubuntu 18.04 to 20.04. Since then, It is stuck in loading forever when starting normally. I started successfully from recovery mode, 

The boot problem is not my main issue: My main issue is when logging in to my company via SSH. The SSH connection gets heavily stuck since the upgrade. Working is really hard. It works sometimes immediately but can get a 10s+ delay when I try to send any input. Sometimes it cuts off with a 'broken pipe' error, I guess by the server for my side being 'unresponsive'. This problem appears on my side (my colleagues are fine) and is no general network problem - any other network usage is perfect. I'm just unsure if recovery mode might have something to do with it - what should I do to analyse this issue and fix it?

Thank you & best regards, 
Alfred

---

### Post by TheFu on 2020-10-15
ssh -vvv?

---

### Post by alfred-holzherr on 2020-10-15
Thanks, that's a great start.

There doesn't seem to be a lot of issues in the debug messages. It does give 'debug1: Unspecified GSS failure.  Minor code may provide more information. No Kerberos credentials available', but I'm doubtful that's related.

My working hypothesis is, that the missing graphics driver from the recovery boot is causing problems, though I don't really know how this should affect just the SSH terminal. Maybe a network driver is also different in recovery mode? Graphics-intensive software does however also get stuck in a similar way, as I just tested. (I guess that's expected behaviour in recovery mode - I just didn't expect SSH issues.) 

I tried sudo gedit /etc/gdm3/custom.conf --> #WaylandEnable=false to WaylandEnable=false --> reboot to check display server with no improvement on the boot issue. (Rebooting via Recovery Mode also didn't improve my SSH issues, which still hangs all the time. Non-graphic applications (e.g. Matlab computations, Firefox) are responding smoothly, so it's no general performance problem.)

---

### Post by TheFu on 2020-10-15
GPU stuff has nothing to do with ssh.  The GSS problem is more likely.  Look up with a web search.  It can be disabled in the ssh_config file or in your ~/.ssh/config if you prefer. Just put "GSSAPIAuthentication no" over /etc/ssh/ssh_config 

Don't edit system files with **sudo {some-gui-editor}**.  That can lead to issues.  Use **sudoedit** to edit system files. sudoedit honors the EDITOR environment variable. Just set that to whatever editor you like. However, if you choose a GUI editor, then I don't think it will work over ssh.

GUI questions need a different thread. That's a completely different skillset. I can't help with GUI stuff. Not my thing and I barely use them.

---

### Post by alfred-holzherr on 2020-10-15
Thanks a lot, also for the advice for the editor!

I put SSAPIAuthentication no in /etc/ssh/ssh_config, the error message disappears, but my 'delays & connectivity' problem persists.

I post the full -vvv debug log here, but it'm out of time for now and will get back tomorrow. Thank you a lot so far :)


```
OpenSSH_8.2p1 Ubuntu-4ubuntu0.1, OpenSSL 1.1.1f  31 Mar 2020
debug2: resolving "{PRIVATE}" port 22
debug2: ssh_connect_direct
debug1: Connecting to {PRIVATE} port 22.
debug1: Connection established.
debug1: identity file {PRIVATE}.ssh/id_rsa type 0
debug1: identity file {PRIVATE}.ssh/id_rsa-cert type -1
debug1: identity file {PRIVATE}.ssh/id_dsa type -1
debug1: identity file {PRIVATE}.ssh/id_dsa-cert type -1
debug1: identity file {PRIVATE}.ssh/id_ecdsa type -1
debug1: identity file {PRIVATE}.ssh/id_ecdsa-cert type -1
debug1: identity file {PRIVATE}.ssh/id_ecdsa_sk type -1
debug1: identity file {PRIVATE}.ssh/id_ecdsa_sk-cert type -1
debug1: identity file {PRIVATE}.ssh/id_ed25519 type -1
debug1: identity file {PRIVATE}/.ssh/id_ed25519-cert type -1
debug1: identity file {PRIVATE}.ssh/id_ed25519_sk type -1
debug1: identity file {PRIVATE}.ssh/id_ed25519_sk-cert type -1
debug1: identity file {PRIVATE}.ssh/id_xmss type -1
debug1: identity file {PRIVATE}.ssh/id_xmss-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_8.2p1 Ubuntu-4ubuntu0.1
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.4
debug1: match: OpenSSH_7.4 pat OpenSSH_7.0*,OpenSSH_7.1*,OpenSSH_7.2*,OpenSSH_7.3*,OpenSSH_7.4*,OpenSSH_7.5*,OpenSSH_7.6*,OpenSSH_7.7* compat 0x04000002
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to {PRIVATE}:22 as '{PRIVATE}
debug3: hostkeys_foreach: reading file "/{PRIVATE}.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file {PRIVATE}.ssh/known_hosts:40
debug3: load_hostkeys: loaded 1 keys from fh2.scc.kit.edu
debug3: order_hostkeyalgs: prefer hostkeyalgs: {}
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: {}
debug2: host key algorithms: {}
debug2: ciphers ctos: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email]
debug2: ciphers stoc: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email]
debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: {}
debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email],aes128-cbc,aes192-cbc,aes256-cbc,blowfish-cbc,cast128-cbc,3des-cbc
debug2: ciphers stoc: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email],aes128-cbc,aes192-cbc,aes256-cbc,blowfish-cbc,cast128-cbc,3des-cbc
debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: {PRIVATE}
debug1: kex: host key algorithm: {PRIVATE}
debug1: kex: server->client cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> compression: none
debug1: kex: client->server cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> compression: none
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: Server host key: {PRIVATE}
debug3: hostkeys_foreach: reading file "/{PRIVATE}.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file {PRIVATE}.ssh/known_hosts:40
debug3: load_hostkeys: loaded 1 keys from {PRIVATE}
debug3: hostkeys_foreach: reading file "/{PRIVATE}.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /{PRIVATE}.ssh/known_hosts:39
debug3: load_hostkeys: loaded 1 keys from {PRIVATE}
debug1: Host '{PRIVATE}' is known and matches the ECDSA host key.
debug1: Found key in /{PRIVATE}.ssh/known_hosts:40
Warning: the ECDSA host key for '{PRIVATE}' differs from the key for the IP address '{PRIVATE}'
Offending key for IP in {PRIVATE}.ssh/known_hosts:39
Matching host key in {PRIVATE}.ssh/known_hosts:40
Are you sure you want to continue connecting (yes/no)? yes
ebug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey out after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug1: SSH2_MSG_NEWKEYS received
debug2: set_newkeys: mode 0
debug1: rekey in after 134217728 blocks
debug1: Will attempt key: {}
debug2: pubkey_prepare: done
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs={}
debug3: receive packet: type 6
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug3: send packet: type 50
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,keyboard-interactive
debug3: start over, passed a different list publickey,gssapi-keyex,gssapi-with-mic,keyboard-interactive
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key:{} agent
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,keyboard-interactive
debug1: Trying private key: {}
debug2: we did not send a packet, disable method
debug3: authmethod_lookup keyboard-interactive
debug3: remaining preferred: password
debug3: authmethod_is_enabled keyboard-interactive
debug1: Next authentication method: keyboard-interactive
debug2: userauth_kbdint
debug3: send packet: type 50
debug2: we sent a keyboard-interactive packet, wait for reply
debug3: receive packet: type 60
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 1
your OTP: {}
debug3: send packet: type 61
debug3: receive packet: type 60
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 1
Password: {}
debug3: send packet: type 61
debug3: receive packet: type 60
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 0
debug3: send packet: type 61
debug3: receive packet: type 52
debug1: Authentication succeeded (keyboard-interactive).
Authenticated to {}
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug3: send packet: type 90
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug3: send packet: type 80
debug1: Entering interactive session.
debug1: pledge: network
debug3: receive packet: type 80
debug1: client_input_global_request: rtype [EMAIL="hostkeys-00@openssh.com"]hostkeys-00@openssh.com[/EMAIL] want_reply 0
debug3: receive packet: type 91
debug2: channel_input_open_confirmation: channel 0: callback start
debug2: fd 3 setting TCP_NODELAY
debug3: ssh_packet_set_tos: set IPV6_TCLASS 0x10
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug3: send packet: type 98
debug2: channel 0: request shell confirm 1
debug3: send packet: type 98
debug2: channel_input_open_confirmation: channel 0: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug3: receive packet: type 99
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug3: receive packet: type 99
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Last login: Thu Oct 15 15:56:59 2020 from {}
```

---

### Post by ActionParsnip on 2020-10-15
Is the CPU and/or RAM overstretched on the server side?

---

### Post by alfred-holzherr on 2020-10-15
I have a ticket open at their service desk, they already told me that I'm the only user with this complaint at the moment, and thus 'likely not on their end'. But maybe it is, and just coincidental with my upgrade - stuff happens. The cluster is used by ~ 4000 users, but much less than usual today - so if they do have a problem, it might have gone unnoticed.

Update: I finally got a social media statement from one of my colleagues who is having similar issues. So it seems to me, it is the server.

---

### Post by TheFu on 2020-10-15
Fix this:
```

debug1: Found key in /{PRIVATE}.ssh/known_hosts:40
Warning: the ECDSA host key for '{PRIVATE}' differs from the key for the IP address '{PRIVATE}'
Offending key for IP in {PRIVATE}.ssh/known_hosts:39
Matching host key in {PRIVATE}.ssh/known_hosts:40
Are you sure you want to continue connecting (yes/no)? yes
```

ssh servers can reject bogus client-side key exchange.

btw, using code tag here would be appreciated.

---

