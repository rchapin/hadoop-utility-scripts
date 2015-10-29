# Hadoop Utility Scripts

**By:** Ryan Chapin [Contact Info](http://www.ryanchapin.com/contact.html)

Utility scripts for a local hadoop/hdfs development environment for managing hdfs and hadoop applications in a pseudo-distributed installation.

Currently includes the following utilities:

- **hadoop-services**:  Manages the execution of groups of init scripts for hadoop services.  Currently supports:

  * hdfs - the HDFS file system daemons
  * mr   - the MapReduce applicaton daemons

```
Usage: hadoop-services [OPTIONS] -d [daemon-group] -c [init-command]

  -d daemon-group [hdfs|mr]

  -c init script command to execute [start|stop|status]

Options:
  -h HELP
    Outputs this basic usage information.

  -s SILENT
    Silence all STDOUT from each init script

  --more-help EXTENDED HELP
    Extended help and documentation.
```

- **hdfs-reformat**:  Will reformat, completely destroying the existing HDFS on the local, pseudo-distributed installation.  Will also prompt for creation of (multiple, if desired) non-root user 'home' directories on hdfs.

```
hdfs-reformat - format/reformat  local  hdfs  in  a  Cloudera   pseudo-distributed
              installation.  Must be run as root.  Currently supports  CDH 4 and
              above.

Usage: hdfs-reformat [OPTIONS]

Options:

  --force FORCE_WITHOUT_PROMPT
    Automatically reformat without prompting for confirmation.  Running in this
    mode will preclude the option of creating non-root user 'home' dir on hdfs.

  -h HELP
    Outputs this basic usage information.

  -s SILENT
    Silence all STDOUT from each init script

  --more-help EXTENDED HELP
    Extended help and documentation.

Extended Usage:

  Will reformat the local hdfs file system and optionally allow for the creation
  of non-root user 'home' directories on HDFS.

  When prompted as to whether or not to create a non-root user account,  if  the
  name of the user-id input is  'rchapin', the script will create  the following
  directory on hdfs: /user/rchapin, and set the permissions for the user of that
  same name.

Example:

  # hdfs-reformat
  Will prompt for confirmation to reformat hdfs

  # hdfs-reformat --force -s
  Will not prompt for confirmation to reformat hdfs and will surpress all STDOUT
  and STDERR
```

- Additional files:

  * hadoop-utility-functions: self-explanatory
  * mr-version: configuration file for the list of MapReduce daemon init scripts for either MRv1 or MRv2


## To Configure and Install

After unpacking the distribution .zip or tarball:

1.  Copy all of the files to a directory that is in root's path (/usr/local/sbin) and ensure that they are executable.

2.  Confirm that the configurations in hdfs-reformat are correct for your system.

## To Run

Executing either ```hadoop-services -h``` or ```hdfs-reformat -h``` will provide the documentation.
