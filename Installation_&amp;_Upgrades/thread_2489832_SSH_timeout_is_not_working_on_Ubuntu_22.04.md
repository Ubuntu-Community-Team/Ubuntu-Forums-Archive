---
title: "SSH timeout is not working on Ubuntu 22.04"
date: 2023-08-11
forum: Installation &amp; Upgrades
---

### Post by prashanma on 2023-08-11
Hi Team,

SSH idle timeout is not working on Ubuntu 22.04 
Following are my configuration

This is our /etc/profile config
TMOUT=60
readonly TMOUT
export TMOUT

cat /etc/bash.bashrc
umask 027
TMOUT=900
readonly TMOUT
export TMOUT

cat /etc/ssh/sshd_config
#TCPKeepAlive yes
ClientAliveInterval 60
ClientAliveCountMax 0

Can anyone helpout here ? 

Regards 
MA

---

### Post by MAFoElffen on 2023-08-12
have you tested it by just setting the override option in the connect string?
```

ssh -o ConnectTimeout=10 <username>@<hostName>

```

---

### Post by prashanma on 2023-08-14
it is not working as well. Work only bash.bashrc related config. Is this a bug in a ubuntu 22.04 ?

---

### Post by MAFoElffen on 2023-08-15
Well... No. I misunderstood which setting you were asking about
```

mafoelffen@msi-ubuntu:~$ grep -i alive /etc/ssh/sshd_config
#TCPKeepAlive yes
#ClientAliveInterval 0
#ClientAliveCountMax 3

```
These used to be 'KeepAlive', the changed.

RE : [Ubuntu Man Page sshd_config]("https://manpages.ubuntu.com/manpages/xenial/man5/sshd_config.5.html")
```

     TCPKeepAlive
             Specifies whether the system should send TCP keepalive messages to the other side.
             If they are sent, death of the connection or crash of one of the machines will be
             properly noticed.  However, this means that connections will die if the route is
             down temporarily, and some people find it annoying.  On the other hand, if TCP
             keepalives are not sent, sessions may hang indefinitely on the server, leaving
             &#8220;ghost&#8221; users and consuming server resources.

             The default is &#8220;yes&#8221; (to send TCP keepalive messages), and the server will notice if
             the network goes down or the client host crashes.  This avoids infinitely hanging
             sessions.

             To disable TCP keepalive messages, the value should be set to &#8220;no&#8221;.

             This option was formerly called KeepAlive.

     ClientAliveCountMax
             Sets the number of client alive messages (see below) which may be sent without
             sshd(8) receiving any messages back from the client.  If this threshold is reached
             while client alive messages are being sent, sshd will disconnect the client,
             terminating the session.  It is important to note that the use of client alive
             messages is very different from TCPKeepAlive (below).  The client alive messages are
             sent through the encrypted channel and therefore will not be spoofable.  The TCP
             keepalive option enabled by TCPKeepAlive is spoofable.  The client alive mechanism
             is valuable when the client or server depend on knowing when a connection has become
             inactive.

             The default value is 3.  If ClientAliveInterval (see below) is set to 15, and
             ClientAliveCountMax is left at the default, unresponsive SSH clients will be
             disconnected after approximately 45 seconds.

     ClientAliveInterval
             Sets a timeout interval in seconds after which if no data has been received from the
             client, sshd(8) will send a message through the encrypted channel to request a
             response from the client.  The default is 0, indicating that these messages will not
             be sent to the client.

```
So according to the man page, what I posted is the default settings, even though they are commented out.

So your settings of
```

#TCPKeepAlive yes  ## Default is already set to yes, which sends messages. If you didn't want this, you would have to set to 'no'.
ClientAliveInterval 60  ## Says it will send a message if no data is sent in 60 seconds
ClientAliveCountMax 0  ## Default is 3, but you set at 0, which turned it off. So conflicts with your ClientAliveInterval setting...

```
If you set your ClientAliveMaxCount 1, it will send one message after 60 seconds of idle time, and disconnect if there is no response.

---

