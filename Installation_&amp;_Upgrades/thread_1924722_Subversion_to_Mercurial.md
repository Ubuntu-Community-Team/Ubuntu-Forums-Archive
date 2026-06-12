---
title: "Subversion to Mercurial"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by auny on 2012-02-13
i am having some problem in converting my svn repo to mercurial.
can anyone please help me.
when i run this command nothing happens.
i have installed 
subversion: 1.6.12
hgsvn: 0.1.10
hgsubversion: 1.3+9-4e203a47102a
mercurial: 2.1

aun@ubuntu:/var/hg/repos/$ sudo hgimportsvn [http://192.168.64.130/svn/dir4hg/trunk](http://192.168.64.130/svn/dir4hg/trunk) myrepo
[sudo] password for aun: 
Password for 'admin': 
admin
admin

^CTraceback (most recent call last):
  File "/usr/local/bin/hgimportsvn", line 9, in <module>
    load_entry_point('hgsvn==0.1.10.dev', 'console_scripts', 'hgimportsvn')()
  File "/usr/local/lib/python2.7/dist-packages/hgsvn-0.1.10.dev-py2.7.egg/hgsvn/run/hgimportsvn.py", line 69, in main
    svn_info = get_svn_info(target_svn_url, options.svn_rev)
  File "/usr/local/lib/python2.7/dist-packages/hgsvn-0.1.10.dev-py2.7.egg/hgsvn/svnclient.py", line 155, in get_svn_info
    fail_if_stderr=True)
  File "/usr/local/lib/python2.7/dist-packages/hgsvn-0.1.10.dev-py2.7.egg/hgsvn/common.py", line 254, in run_svn
    args=args, bulk_args=bulk_args, fail_if_stderr=fail_if_stderr)
  File "/usr/local/lib/python2.7/dist-packages/hgsvn-0.1.10.dev-py2.7.egg/hgsvn/common.py", line 174, in run_command
    return _run_raw_command(cmd, map(_transform_arg, args), fail_if_stderr)
  File "/usr/local/lib/python2.7/dist-packages/hgsvn-0.1.10.dev-py2.7.egg/hgsvn/common.py", line 141, in _run_raw_command
    out, err = pipe.communicate()
  File "/usr/lib/python2.7/subprocess.py", line 740, in communicate
    return self._communicate(input)
  File "/usr/lib/python2.7/subprocess.py", line 1276, in _communicate
    stdout, stderr = self._communicate_with_poll(input)
  File "/usr/lib/python2.7/subprocess.py", line 1330, in _communicate_with_poll
    ready = poller.poll()
KeyboardInterrupt
aun@ubuntu:/var/hg/repos/1$ 

can anyone tell me which package i have to install, to successfully complete my conversion.
thnx in advance.

---

### Post by auny on 2012-02-17
is there no one to help me???
or at least give me an answer
thanks

---

