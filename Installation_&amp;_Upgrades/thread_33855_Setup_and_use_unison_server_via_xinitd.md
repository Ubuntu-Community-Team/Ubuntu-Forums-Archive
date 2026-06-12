---
title: "Setup and use unison server via xinitd"
date: 2005-05-12
forum: Installation &amp; Upgrades
---

### Post by dacosta123 on 2005-05-12
Hi,

I'm struggling a bit with 'connecting' to a unison server in a chroot jail started up via xinetd.
Following the xinetd code
service unison
{
        flags = NAMEINARGS
        env = HOME=/ UNISON=/.unison PATH=/bin
        passenv =
        log_on_success = HOST PID DURATION USERID
        log_on_failure = HOST RECORD USERID
        port = 7654
        socket_type = stream
        protocol = tcp
        user = root
        group = unision
        server = /usr/sbin/tcpd
        server_args = /usr/sbin/chroot /home/unison /bin/unison -server
        type = UNLISTED
        wait = no
        instances = 1
}

Next i run /etc/init.d/xinet restart to get the thing to go 'in the air'.

Using netstat a- however i do not see the port 7654 being listened on.
The folowing command:
unison -testServer foo socket://localhost:7654//foo && echo Horray!
just replies with:
Contacting server...
p = .viminfo; bn = .viminfo
Fatal error: Can't connect to server (localhost):

Any suggestions?
tia,
Fermin DCG

ps. If this is not the correct forum please let me know and i'll 'move' my question

---

### Post by dacosta123 on 2005-05-13
Looked into the /var/log/syslog and saw that some typos were to blame  ](*,) 

Still got some work to do on a version issue (ubuntu is lagging somewhat)

---

