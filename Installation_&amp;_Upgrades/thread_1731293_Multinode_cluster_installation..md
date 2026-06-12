---
title: "Multinode cluster installation."
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by sandyHadoop on 2011-04-17
Hello everyone.
I have facing a problem on installation of hadoop multinode cluster. I have installed single node cluster in 2 machines and configured the conf folder of both machines. i have taken one as master machine and another as slave. When i execute start-all.sh on master machine all the parameters are enabled properly on master but didnt enable on slave. When i execute start-all.sh on master iam getting eror that cannot copy log files into slave. 

The error is as below,

 hadoop@user-G41M-Combo:/usr/local/hadoop/hadoop$ bin/start-all.sh
namenode running as process 25724. Stop it first.
slave: mv: cannot move `/usr/local/hadoop/hadoop/bin/../logs/hadoop-hadoop-datanode-user-HP-dx2480-MT-NA125PA.out' to `/usr/local/hadoop/hadoop/bin/../logs/hadoop-hadoop-datanode-user-HP-dx2480-MT-NA125PA.out.1': Permission denied
slave: starting datanode, logging to /usr/local/hadoop/hadoop/bin/../logs/hadoop-hadoop-datanode-user-HP-dx2480-MT-NA125PA.out
master: starting datanode, logging to /usr/local/hadoop/hadoop/bin/../logs/hadoop-hadoop-datanode-user-G41M-Combo.out
slave: log4j:ERROR Failed to rename [/usr/local/hadoop/hadoop/bin/../logs/hadoop-hadoop-datanode-user-HP-dx2480-MT-NA125PA.log] to [/usr/local/hadoop/hadoop/bin/../logs/hadoop-hadoop-datanode-user-HP-dx2480-MT-NA125PA.log.2011-04-11].
master: starting secondarynamenode, logging to /usr/local/hadoop/hadoop/bin/../logs/hadoop-hadoop-secondarynamenode-user-G41M-Combo.out
jobtracker running as process 27006. Stop it first.
slave: mv: cannot move `/usr/local/hadoop/hadoop/bin/../logs/hadoop-hadoop-tasktracker-user-HP-dx2480-MT-NA125PA.out' to `/usr/local/hadoop/hadoop/bin/../logs/hadoop-hadoop-tasktracker-user-HP-dx2480-MT-NA125PA.out.1': Permission denied
slave: starting tasktracker, logging to /usr/local/hadoop/hadoop/bin/../logs/hadoop-hadoop-tasktracker-user-HP-dx2480-MT-NA125PA.out
master: starting tasktracker, logging to /usr/local/hadoop/hadoop/bin/../logs/hadoop-hadoop-tasktracker-user-G41M-Combo.out
slave: log4j:ERROR Failed to rename [/usr/local/hadoop/hadoop/bin/../logs/hadoop-hadoop-tasktracker-user-HP-dx2480-MT-NA125PA.log] to [/usr/local/hadoop/hadoop/bin/../logs/hadoop-hadoop-tasktracker-user-HP-dx2480-MT-NA125PA.log.2011-04-11].


Could you please help me solve this problem.

Thank you.

---

