---
title: "cant install Hbase."
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by sandyHadoop on 2011-03-18
Hi..

I have configured Hadoop for single node cluster and when l run these URL's [http://localhost:50030/jobtracker.jsp](http://localhost:50030/jobtracker.jsp) ,[http://localhost:50060/tasktracker.jsp](http://localhost:50060/tasktracker.jsp) ,[http://localhost:50070/dfshealth.jsp](http://localhost:50070/dfshealth.jsp)
the web pages are opening, which means that Hadoop is configured.
I have followed " [http://jwm.slavitica.net/p/projects/...ngle_Server%29](http://jwm.slavitica.net/p/projects/...ngle_Server%29) " for cofiguring hadoop single node cluster.

Now i want to install HBASE for this.So when i tried the command to install Hbase " sudo /usr/lib/hbase/bin/start-hbase.sh " I got an error that " hadoop is not in the sudoers file. This incident will be reported. "
So i changed the authentication of Hadoop to Administrator. But now when iam trying to execute the " sudo /usr/lib/hbase/bin/start-hbase.sh " command its is asking for " root@localhost's password: " .
Iam following " [http://ria101.wordpress.com/2010/01/...t-java-client/](http://ria101.wordpress.com/2010/01/...t-java-client/) " to install HBASE for Hadoop single node cluster.

So please help me to install Hbase for single node cluster or else please please tell me whether i have gone wrong somewhere...

Thanks in advance.

---

