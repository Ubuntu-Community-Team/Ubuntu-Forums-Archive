---
title: "Problem with installing Hbase."
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by sandyHadoop on 2011-03-17
Hi..

I have configured Hadoop for single node cluster and when l run these URL's [http://localhost:50030/jobtracker.jsp](http://localhost:50030/jobtracker.jsp) ,[http://localhost:50060/tasktracker.jsp](http://localhost:50060/tasktracker.jsp) ,[http://localhost:50070/dfshealth.jsp](http://localhost:50070/dfshealth.jsp)
the web pages are opening, whch means that Hadoop is configured.
I have followed " [http://jwm.slavitica.net/p/projects/...ngle_Server%29](http://jwm.slavitica.net/p/projects/...ngle_Server%29) " for cofiguring single node cluster.

Now i want to install HBASE for Hadoop single node cluster.So when i tried to install Hbase after all confugurations using command " sudo /usr/lib/hbase/bin/start-hbase.sh " I got an error that " hadoop is not in the sudoers file. This incident will be reported. "
So i changed the authentication of Hadoop to Administrator. But now when iam trying to execute the " sudo /usr/lib/hbase/bin/start-hbase.sh " command its is asking for " root@localhost's password: " .
Iam following " [http://ria101.wordpress.com/2010/01/...t-java-client/](http://ria101.wordpress.com/2010/01/...t-java-client/) " to install HBASE for Hadoop single node cluster.

So please help me to install Hbase for single node cluster or else please please tell me whether i have gone wrong somewhere...

Thanks in advance.

---

