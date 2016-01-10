nagios_check_open_files
=======================

This is a Nagios-check which verify if there are to many opened for a given user. For me this was necessary to check an application server [http://wildfly.org/]. Its also useful for monitoring the server and fine tune it.

Installation
--------------
Add the following to the sudoers file to grand permissions to lsof and to read the file limits from /proc/PID/limits. This can also be done for the nagios user.

```
Cmnd_Alias NRPE_CHECK_OPEN_FILES = /bin/cat /proc/*/limits, /sbin/lsof -u *

nrpe    ALL=(ALL) NOPASSWD: NRPE_CHECK_OPEN_FILES
```

Usage
-------
```
./check_open_files.sh <username>
```
Example:
```
./check_open_files.sh apache
```
