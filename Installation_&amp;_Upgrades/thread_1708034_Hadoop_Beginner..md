---
title: "Hadoop Beginner."
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by sandeepa_mds on 2011-03-16
Hi.

Iam beginner to Hadoop I have installed UBUNTU in my system. I have configured Hadoop for single node cluster and when l  run these URL's  [http://localhost:50030/jobtracker.jsp ,]("http://localhost:50030/jobtracker.jsp")[http://localhost:50060/tasktracker.jsp ,]("http://localhost:50060/tasktracker.jsp")[http://localhost:50070/dfshealth.jsp](http://localhost:50070/dfshealth.jsp)
 the  web pages are opening, whch means that Hadoop is configured. 
I have followed "  [http://jwm.slavitica.net/p/projects/research/wiki/Hadoop_Install_%28Single_Server%29](http://jwm.slavitica.net/p/projects/research/wiki/Hadoop_Install_%28Single_Server%29)  " for cofiguring single node cluster.

Now i want to install HBASE for this.So when i tried the command to install  " sudo  /usr/lib/hbase/bin/start-hbase.sh " I got an error that " hadoop is not in the sudoers file.  This incident will be reported. "
So i changed the authentication of Hadoop to Administratop. But  now when iam trying to execute the " sudo  /usr/lib/hbase/bin/start-hbase.sh " command its is asking for " root@localhost's password: "  . 
 Iam following " [http://ria101.wordpress.com/2010/01/28/setup-hbase-in-pseudo-distributed-mode-and-connect-java-client/](http://ria101.wordpress.com/2010/01/28/setup-hbase-in-pseudo-distributed-mode-and-connect-java-client/) " to install HBASE for Hadoop single node cluster. 

So please help me to install Hbase for single node cluster or else please please tell me whether i have  gone wrong somewhere...

Thanks in advance.

---

### Post by KMPSJHS on 2012-08-15
hi,

I am also installing hadoop single node cluster.i typed this code "sudo /etc/init.d/ssh reload".I got the same message as you got "hduser is not in the sudoers file.this incident will be reported." what should i do to solve this problem?

actually i wants to install chukwa tool in ubuntu for log collection in cluster mode. Am i need to configure the whole hadoop single node cluster environment for installing chukwa?

---

### Post by riverfr0zen on 2012-08-15
> **sandeepa_mds said:**
> 
Now i want to install HBASE for this.So when i tried the command to install  " sudo  /usr/lib/hbase/bin/start-hbase.sh " I got an error that " hadoop is not in the sudoers file.  This incident will be reported. "
So i changed the authentication of Hadoop to Administratop. But  now when iam trying to execute the " sudo  /usr/lib/hbase/bin/start-hbase.sh " command its is asking for " root@localhost's password: "  . 
Iam following " [http://ria101.wordpress.com/2010/01/28/setup-hbase-in-pseudo-distributed-mode-and-connect-java-client/](http://ria101.wordpress.com/2010/01/28/setup-hbase-in-pseudo-distributed-mode-and-connect-java-client/) " to install HBASE for Hadoop single node cluster. 


I don't see anywhere in that article where it tells you to start h-base using sudo. It says to log in as the hadoop user, and just run /usr/lib/hbase/bin/start-hbase.sh

@KMPSJHS:

You just need to add hduser to the sudoers file. See [http://www.pendrivelinux.com/how-to-add-a-user-to-the-sudoers-list/](http://www.pendrivelinux.com/how-to-add-a-user-to-the-sudoers-list/)

---

