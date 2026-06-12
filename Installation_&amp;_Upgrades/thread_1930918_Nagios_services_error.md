---
title: "Nagios services error"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by bmidlock on 2012-02-24
Hello all

I have Nagios installed on an Ubuntu machine. Im setting up some of our servers, I have 2 set up so far. Both are windows OS.

On one of the servers Im getting an unknown status for the disk drive space and explorer. The server that Im getting an error on is a 64 bit machine running windows server 2008 r2. 


define service{
        use                     generic-service
        host_name               MQ1
        service_description     C:\ Drive Space
        check_command           check_nt!USEDDISKSPACE!-1 c -w 80 -c 90
        }


define service{
        use                     generic-service
        host_name               MQ1
        service_description     Explorer
        check_command           check_nt!PROCSTATE!-d SHOWALL -1 Explorer.exe
        }

Thanks in advance!

---

### Post by gordintoronto on 2012-02-24
I think you are asking Ubuntu users to solve a Windows problem. Perhaps there are better forums for finding help with Windows.

---

