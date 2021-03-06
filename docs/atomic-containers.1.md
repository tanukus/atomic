% ATOMIC(1) Atomic Man Pages
% Giuseppe Scrivano
% June 2016
# NAME
atomic-containers - operations on containers

# SYNOPSIS
**atomic containers COMMAND [OPTIONS] [CONTAINERS...]**

atomic containers allows the user to view and operate on containers

# COMMANDS
**delete**

delete specified container(s).

**list**

list containers on your system.

**trim**

discard unused blocks (fstrim) on running containers.

**update**

update a system container.

**rollback**

rollback a system container.

# DESCRIPTION
**atomic containers delete**, delete specified container image from the system.

Using --all will delete all the installed containers.

**atomic containers list**, by default, will list all running containers on your
system.

Using --all will list all the installed containers.

**atomic containers trim**, Discard unused blocks (fstrim) on rootfs of running containers.

e.g. If you have 2 running containers on your system with container IDs (496b8679b6cf, 9bb990da1203).

>atomic containers trim
Trimming container id 496b8679b6cf
Trimming container id 9bb990da1203

**atomic containers update**, update a system container to use a newer version of an image.

Can use --set to update environment variables.

**atomic containers rollback**, rollback a system container to the other deployment if one exists.

# OPTIONS:
**-h** **--help**
  Print usage statement

# delete OPTIONS:
**-a** **--all**
  Delete all the installed containers

**-f** **--force**
  Force the deletion of specified running containers

# list OPTIONS:
**-a** **--all**
  Print all the installed containers

**-f** **--filter**
  Filter output based on given filters, example usage: `--filter container=foo` will list all containers that has "foo" as part of their container ID.

  Filterables: `backend`, `command`, `container`, `created`, `image`, `runtime`, `state`

**--json**
  Print in a machine parsable format

**-n** **--noheading**
  Do not print heading when listing the containers

**--no-trunc**
  Do not truncate output

**-q** **--quiet**
  Only display container IDs

# update OPTIONS:
**--rebase=IMAGE**
  Rebase to a different image.  If not specified, the same image used to install the container will be used.

**-a** **--all**
  Update all the installed containers.  If any update fails, then it rollbacks automatically to the working version of the container.

**--set=NAME=VALUE**
  Set a value that is going to be used by a system container for its configuration and can be specified multiple times.  OSTree is required for this feature to be available.

# HISTORY
June 2016, Originally compiled by Giuseppe Scrivano (gscrivan at redhat dot com)
July 2016, Added sub-commands filter, no-trunc and quiet (jerzhang at redhat dot com)
Sept 2016, Added atomic containers trim subcommand (shishir dot mahajan at redhat dot com)
