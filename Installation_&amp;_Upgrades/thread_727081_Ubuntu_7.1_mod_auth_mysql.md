---
title: "Ubuntu 7.1 mod_auth_mysql"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by randomorbit on 2008-03-17
Hi.  I've spent hours trying to find a solution to this, so if it's posted somewhere, please let me know.  I am trying to get mod_auth_mysql to install under 7.10, but I keep getting the following errors:

randomorbit@cp-srv2:~/mod_auth_mysql-3.0.0$ apxs2 -c -DHOST=localhost -lmysqlclient -lm -lz m
od_auth_mysql.c
/usr/share/apr-1.0/build/libtool --silent --mode=compile --tag=disable-static i486-linux-gnu-gcc -prefer-pic -DLINUX=2 -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -D_REENTRANT -I/usr/include/apr-1.0 -I/usr/include/openssl -I/usr/include/postgresql -I/usr/include/xmltok -pthread     -I/usr/include/apache2  -I/usr/include/apr-1.0   -I/usr/include/apr-1.0 -I/usr/include/postgresql -DHOST=localhost  -c -o mod_auth_mysql.lo mod_auth_mysql.c && touch mod_auth_mysql.slo
mod_auth_mysql.c:269:19: error: mysql.h: No such file or directory
mod_auth_mysql.c:379: error: expected specifier-qualifier-list before 'MYSQL'
mod_auth_mysql.c:386: warning: excess elements in struct initializer
mod_auth_mysql.c:386: warning: (near initialization for 'connection')
mod_auth_mysql.c:386: warning: excess elements in struct initializer
mod_auth_mysql.c:386: warning: (near initialization for 'connection')
mod_auth_mysql.c:386: warning: excess elements in struct initializer
mod_auth_mysql.c:386: warning: (near initialization for 'connection')
mod_auth_mysql.c:386: warning: excess elements in struct initializer
mod_auth_mysql.c:386: warning: (near initialization for 'connection')
mod_auth_mysql.c: In function 'close_connection':
mod_auth_mysql.c:396: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:397: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:398: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c: In function 'open_db_handle':
mod_auth_mysql.c:453: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'mysql_conn'
mod_auth_mysql.c:453: error: 'mysql_conn' undeclared (first use in this function)
mod_auth_mysql.c:453: error: (Each undeclared identifier is reported only once
mod_auth_mysql.c:453: error: for each function it appears in.)
mod_auth_mysql.c:458: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:462: error: 'mysql_connection' has no member named 'host'
mod_auth_mysql.c:466: error: 'mysql_connection' has no member named 'host'
mod_auth_mysql.c:471: error: 'mysql_connection' has no member named 'user'
mod_auth_mysql.c:475: error: 'mysql_connection' has no member named 'user'
mod_auth_mysql.c:481: error: 'mysql_connection' has no member named 'db'
mod_auth_mysql.c:486: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:487: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:491: error: 'mysql_connection' has no member named 'db'
mod_auth_mysql.c:500: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:501: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:506: error: 'mysql_connection' has no member named 'host'
mod_auth_mysql.c:508: error: 'mysql_connection' has no member named 'host'
mod_auth_mysql.c:512: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:512: error: 'mysql_connection' has no member named 'host'
mod_auth_mysql.c:520: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:535: error: 'mysql_connection' has no member named 'user'
mod_auth_mysql.c:537: error: 'mysql_connection' has no member named 'user'
mod_auth_mysql.c:539: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:540: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:544: error: 'mysql_connection' has no member named 'db'
mod_auth_mysql.c:548: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:549: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c: In function 'create_mysql_auth_dir_config':
mod_auth_mysql.c:564: error: 'MYSQL_PORT' undeclared (first use in this function)
mod_auth_mysql.c:565: error: 'MYSQL_UNIX_ADDR' undeclared (first use in this function)
mod_auth_mysql.c: At top level:
mod_auth_mysql.c:591: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:591: error: initializer element is not constant
mod_auth_mysql.c:591: error: (near initialization for 'mysql_auth_cmds[0].cmd_data')
mod_auth_mysql.c:595: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:595: error: initializer element is not constant
mod_auth_mysql.c:595: error: (near initialization for 'mysql_auth_cmds[1].cmd_data')
mod_auth_mysql.c:599: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:599: error: initializer element is not constant
mod_auth_mysql.c:599: error: (near initialization for 'mysql_auth_cmds[2].cmd_data')
mod_auth_mysql.c:603: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:603: error: initializer element is not constant
mod_auth_mysql.c:603: error: (near initialization for 'mysql_auth_cmds[3].cmd_data')
mod_auth_mysql.c:607: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:607: error: initializer element is not constant
mod_auth_mysql.c:607: error: (near initialization for 'mysql_auth_cmds[4].cmd_data')
mod_auth_mysql.c:611: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:611: error: initializer element is not constant
mod_auth_mysql.c:611: error: (near initialization for 'mysql_auth_cmds[5].cmd_data')
mod_auth_mysql.c:615: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:615: error: initializer element is not constant
mod_auth_mysql.c:615: error: (near initialization for 'mysql_auth_cmds[6].cmd_data')
mod_auth_mysql.c:619: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:619: error: initializer element is not constant
mod_auth_mysql.c:619: error: (near initialization for 'mysql_auth_cmds[7].cmd_data')
mod_auth_mysql.c:623: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:623: error: initializer element is not constant
mod_auth_mysql.c:623: error: (near initialization for 'mysql_auth_cmds[8].cmd_data')
mod_auth_mysql.c:627: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:627: error: initializer element is not constant
mod_auth_mysql.c:627: error: (near initialization for 'mysql_auth_cmds[9].cmd_data')
mod_auth_mysql.c:631: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:631: error: initializer element is not constant
mod_auth_mysql.c:631: error: (near initialization for 'mysql_auth_cmds[10].cmd_data')
mod_auth_mysql.c:635: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:635: error: initializer element is not constant
mod_auth_mysql.c:635: error: (near initialization for 'mysql_auth_cmds[11].cmd_data')
mod_auth_mysql.c:639: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:639: error: initializer element is not constant
mod_auth_mysql.c:639: error: (near initialization for 'mysql_auth_cmds[12].cmd_data')
mod_auth_mysql.c:643: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:643: error: initializer element is not constant
mod_auth_mysql.c:643: error: (near initialization for 'mysql_auth_cmds[13].cmd_data')
mod_auth_mysql.c:651: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:651: error: initializer element is not constant
mod_auth_mysql.c:651: error: (near initialization for 'mysql_auth_cmds[14].cmd_data')
mod_auth_mysql.c:655: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:655: error: initializer element is not constant
mod_auth_mysql.c:655: error: (near initialization for 'mysql_auth_cmds[15].cmd_data')
mod_auth_mysql.c:659: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:659: error: initializer element is not constant
mod_auth_mysql.c:659: error: (near initialization for 'mysql_auth_cmds[16].cmd_data')
mod_auth_mysql.c:663: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:663: error: initializer element is not constant
mod_auth_mysql.c:663: error: (near initialization for 'mysql_auth_cmds[17].cmd_data')
mod_auth_mysql.c:667: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:667: error: initializer element is not constant
mod_auth_mysql.c:667: error: (near initialization for 'mysql_auth_cmds[18].cmd_data')
mod_auth_mysql.c:671: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:671: error: initializer element is not constant
mod_auth_mysql.c:671: error: (near initialization for 'mysql_auth_cmds[19].cmd_data')
mod_auth_mysql.c: In function 'format_request':
mod_auth_mysql.c:947: warning: pointer/integer type mismatch in conditional expression
mod_auth_mysql.c: In function 'get_mysql_pw':
mod_auth_mysql.c:1020: error: 'MYSQL_RES' undeclared (first use in this function)
mod_auth_mysql.c:1020: error: 'result' undeclared (first use in this function)
mod_auth_mysql.c:1020: error: invalid operands to binary *
mod_auth_mysql.c:1064: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:1065: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:1069: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:1072: error: 'MYSQL_ROW' undeclared (first use in this function)
mod_auth_mysql.c:1072: error: expected ';' before 'data'
mod_auth_mysql.c:1073: error: 'data' undeclared (first use in this function)
mod_auth_mysql.c:1073: error: used struct type value where scalar is required
mod_auth_mysql.c:1074: error: incompatible type for argument 1 of 'atoi'
mod_auth_mysql.c:1076: error: incompatible type for argument 2 of 'memcpy'
mod_auth_mysql.c:1086: error: used struct type value where scalar is required
mod_auth_mysql.c:1087: error: incompatible type for argument 2 of 'apr_pstrdup'
mod_auth_mysql.c: In function 'get_mysql_groups':
mod_auth_mysql.c:1106: error: 'MYSQL_RES' undeclared (first use in this function)
mod_auth_mysql.c:1106: error: 'result' undeclared (first use in this function)
mod_auth_mysql.c:1106: error: invalid operands to binary *
mod_auth_mysql.c:1131: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:1132: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:1136: error: 'mysql_connection' has no member named 'handle'
mod_auth_mysql.c:1142: error: 'MYSQL_ROW' undeclared (first use in this function)
mod_auth_mysql.c:1142: error: expected ';' before 'data'
mod_auth_mysql.c:1143: error: 'data' undeclared (first use in this function)
mod_auth_mysql.c:1143: error: used struct type value where scalar is required
mod_auth_mysql.c:1144: error: incompatible type for argument 2 of 'apr_pstrdup'
apxs:Error: Command failed with rc=65536

Any assistance is greatly appreciated.

Thanks

Mike

---

### Post by jetbadkey on 2008-03-28
I think the line;

> mod_auth_mysql.c:269:19: error: mysql.h: No such file or directory

means you need to add the path to that file.  Should be able to add "-I/usr/include/mysql" to the command.

---

