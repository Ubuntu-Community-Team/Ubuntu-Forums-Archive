---
title: "Ubuntu 16 Plesk Onyx Error"
date: 2017-09-19
forum: Installation &amp; Upgrades
---

### Post by vizuka on 2017-09-19
[FONT=Open Sans Tilde][COLOR=#000000]Does anyone know how to configure a web server on Ubuntu 16 and Plesk Onyx, as I see the curl is missing.
[/COLOR][/FONT]Actually I don't have ssh console. The curl is missing, how to configure curl in plesk without ssh.

If this post in a false subforum please move to the subforum as needed.

[FONT=Open Sans Tilde][COLOR=#000000]Konfigurieren des Webservers nicht möglich:Execution failed. Command: httpdmng Arguments: Array ( [0] => --reconfigure-all ) Details: Curl failed: Timeout was reached Curl failed: Timeout was reached Execution failed. Command: httpdmng Arguments: Array ( [0] => --reconfigure-server [1] => -no-restart ) Details: [2017-09-19 12:29:41] ERR [util_exec] proc_close() failed ['/opt/psa/admin/bin/apache-config' '-t'] with exit code [1] Curl failed: Timeout was reached [2017-09-19 12:30:41] ERR [util_exec] proc_close() failed ['/opt/psa/admin/bin/apache-config' '-t'] with exit code [1] Curl failed: Timeout was reached [2017-09-19 12:31:41] ERR [panel] Apache config (15058169800.99066600) generation failed: Template_Exception: [Tue Sep 19 12:29:41.123831 2017] [:crit] [pid 7635:tid 140262877800320] Apache is running a threaded MPM, but your PHP Module is not compiled to be threadsafe. You need to recompile PHP. AH00013: Pre-configuration failed file: /opt/psa/admin/plib/Template/Writer/Webserver/Abstract.php line: 75 code: 0 Curl failed: Timeout was reached [Tue Sep 19 12:29:41.123831 2017] [:crit] [pid 7635:tid 140262877800320] Apache is running a threaded MPM, but your PHP Module is not compiled to be threadsafe. You need to recompile PHP. AH00013: Pre-configuration failed[/COLOR][/FONT]

---

