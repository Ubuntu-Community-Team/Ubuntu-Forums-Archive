---
title: "Trying to compile simple program, mysql_connect error. anybody help me"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by krisvamc on 2007-05-09
****

Hi,

When I am trying to compile simple **TEST.CC** program I am getting the **mysql_connect error**. Can anybody tell what the error is.

**The code for test.cc is:**

#include <iostream>
#include <fstream>
#include <string>
#include <iomanip.h>
#include <sstream>

#include "mysql/mysql.h"
#include "handling.h"
#include "utils.h"
#include "storage.h"
#include "parser.h"
#include "update.h"
#include "unp.h"
#include "readwrite.h"



using namespace std;


MYSQL mysql;
MYSQL_RES *res;
MYSQL_ROW row;

const unsigned ASM_ADDR = 0xe0000000;
const unsigned ASM_MASK = 4;
const unsigned SSM_ADDR = 0xe8000000;
const unsigned SSM_MASK = 8;

bool CreateDatabase() {
  //Connection to mysql server 
  if (mysql_connect(&mysql,NULL,"root","xxxxx") == NULL) {
    cout << "Error: Couldn't connect to mysql server.";
    return false;
  }
  cout << "Database created successfully." << endl;
  return true;
}


**The error is :**

**root@xxx-laptop:/home/xx/Desktop/xxx# g++ -ansi -pedantic -Wall -W test.cc**
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/iomanip.h:31,
                 from test.cc:4:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
[B]test.cc: In function ‘bool CreateDatabase()’:
test.cc:31: error: ‘mysql_connect’ was not declared in this scope[/B]
root@xxx-laptop:/home/xx/Desktop/xxx# 
[B]
It tells mysql_connect is not declared in this scope. [/B]

thanks.

---

