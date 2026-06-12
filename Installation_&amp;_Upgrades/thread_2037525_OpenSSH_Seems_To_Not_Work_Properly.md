---
title: "OpenSSH Seems To Not Work Properly"
date: 2012-08-04
forum: Installation &amp; Upgrades
---

### Post by Proberts042 on 2012-08-04
I am relatively new to Ubuntu. I recently installed Ubuntu Server 12.04 and am having Openssh problems. I reset the port number in the ssh_config file. when I PuTTy from my laptop to the server I must use port 22. Here is the ssh_config file that I slightly changed.



# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *

#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
        PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no

#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
        Port 222

#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3$
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com

    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
#       Banner /etc/issue.net


It sure seems to me that there should be more uncommented lines in this file. I am using ubuntuserverguide.pdf as a reference. I obtained this file from the Ubuntu 12.04 web site.

Any help will be appreciated.

---

### Post by darkod on 2012-08-04
Did you restart the server after changing the port?

---

### Post by Proberts042 on 2012-08-04
I did restart the server after I made the changes to the file.

---

### Post by darkod on 2012-08-05
The ssh_config file is for the client. The sshd_config file is the configuration for the server.

Look at the blue square warning at the start of the article:
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

You are editing the wrong file.

---

### Post by Proberts042 on 2012-08-05
Hmmmm. I really am a beginner. Thanks so much again.

---

