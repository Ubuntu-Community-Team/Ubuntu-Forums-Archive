---
title: "java Exception Error"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by CupOfItalian on 2013-02-20
Hey guys, 
  I just recently installed metasploit and I am getting an error. 
 The error is:

WARNING: No saved state for javax.swing.JTable

msfgui.MsfException: Database Not Loaded
    at msfgui.MsgRpc.unMsg(MsgRpc.java:102)
    at msfgui.MsgRpc.readResp(MsgRpc.java:134)
    at msfgui.RpcConnection.exec(RpcConnection.java:218)
    at msfgui.RpcConnection.cacheExecute(RpcConnection.java:210)
    at msfgui.RpcConnection.execute(RpcConnection.java:184)
    at msfgui.MainFrame.reloadDb(MainFrame.java:1328)
    at msfgui.MainFrame.access$2000(MainFrame.java:32)
    at msfgui.MainFrame$8.doInBackground(MainFrame.java:464)
    at msfgui.MainFrame$8.doInBackground(MainFrame.java:414)
    at org.jdesktop.swingworker.SwingWorker$1.call(Unknown Source)
    at java.util.concurrent.FutureTask$Sync.innerRun(Unknown Source)
    at java.util.concurrent.FutureTask.run(Unknown Source)
    at org.jdesktop.swingworker.SwingWorker.run(Unknown Source)
    at java.util.concurrent.ThreadPoolExecutor.runWorker(Unknown Source)
    at java.util.concurrent.ThreadPoolExecutor$Worker.run(Unknown Source)
    at java.lang.Thread.run(Unknown Source)

I started both msfrpcd & postgresql but no luck. 

I am pretty sure it has something to do with the either the PATH, or the java gui code. 
Any help would be appreciated.

Thanks

---

### Post by manishiitg on 2013-04-30
which java version are u using?

---

