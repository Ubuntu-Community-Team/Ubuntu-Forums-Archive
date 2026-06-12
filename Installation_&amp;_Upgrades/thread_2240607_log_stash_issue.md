---
title: "log stash issue"
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by aviv2 on 2014-08-21
hi guys, i have installed logstash on my ubuntu 64 bit server and nxlog, i have followed this guides

[https://www.digitalocean.com/community/tutorials/how-to-use-logstash-and-kibana-to-centralize-and-visualize-logs-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-use-logstash-and-kibana-to-centralize-and-visualize-logs-on-ubuntu-14-04)

[https://www.loggly.com/docs/logging-from-windows/](https://www.loggly.com/docs/logging-from-windows/)

everythings works fine till it has lost connection.

it doesn't listen to the logstash port(5000) as i have configured and my nxlog port(6000) is listening on 127.0.0.1.

Foreign Address         State
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:6000          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 192.168.16.22:53        0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN
tcp6       0      0 127.0.0.1:9200          :::*                    LISTEN
tcp6       0      0 127.0.0.1:9301          :::*                    LISTEN
tcp6       0      0 :::53                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 ::1:953                 :::*                    LISTEN


this is my logstash 01-lumberjack-input.conf file

input {
  lumberjack {
    port => 5000
    type => "logs"
    ssl_certificate => "/etc/pki/tls/certs/logstash-forwarder.crt"
    ssl_key => "/etc/pki/tls/private/logstash-forwarder.key"
  }
}


and this is my nxlog config


<Extension _syslog>
    Module      xm_syslog
</Extension>

<Input in1>
    Module      im_udp
    Port        514
    Exec        parse_syslog_bsd();
</Input>

<Input in2>
    Module      im_tcp
    Port        6000
</Input>

<Output fileout1>
    Module      om_file
    File        "/var/log/nxlog/logmsg.txt"
    Exec        if $Message =~ /error/ $SeverityValue = syslog_severity_value("$
    Exec        to_syslog_bsd();
</Output>


i have tried to remove logstash to reinstall without succeed.

---

