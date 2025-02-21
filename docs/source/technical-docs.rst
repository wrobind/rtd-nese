Technical Documentation
=======================


Overview of this Document
-------------------------

This document is a limited summary of technical documentation available directly from NESE
engineering staff to participants in the NESE project, and is intended only for general
orientation about how institutions and researchers access NESE data storage facilities.

If your institution would like to participate in the NESE project, please contact us at
`help@nese.mghpcc.org <mailto:help@mese.mghpcc.org>`_ for current technical documentation and
to establish and obtain your institutional identifiers, Globus accounts, data transfer or
gateway systems, tape storage pools, and so on.

NESE provides data storage with two technologies: Ceph clusters and tape cartridges via an
IBM Spectrum Archive installation. Institutions and researchers can use either or both
storage technologies via the NESE Globus Endpoint or other protocol-specific data transfer nodes
owned by participating institutions.

This document introduces use of the RADOS Block Device for Ceph and discusses the preferred
approach to configuring Globus Collections, Accounts, and Roles to support access to
datasets that are under NESE stewardship.

RADOS Block Device
------------------

RADOS Block Device (RBD) allows Ceph object storage mapping to local block devices using the RBD
kernel module or mapping to a Virtual Machine (VM) via hypervisor that is utilizing direct 
librbd access to the object storage. The mapped block devices could subsequently be accessed for
block storage or formatted with one of the many Linux file systems, therefore exposing the storage
via standard file access methods.

As Ceph architecture does not allow frequent creation and reconfiguration of pools, we will
create one CephX access key and one RBD pool pair per institution or per department and set a
fixed quota at the pool level. CephX access key will allow each institution to use standard rbd
client tools to create and manage RBD images within the given pool.

Globus Configuration
--------------------

The Globus system ultimately allows researchers to easily share large amounts of data with
external collaborators. Project NESE offers Globus institutional endpoint setup with flexible
administrative tasks delegation to its institutional members and researchers.

Delegation of Roles
^^^^^^^^^^^^^^^^^^^

Role delegation hierarchy consists of institutional NESE coordinators, research groups with
shared collections administrators and researchers as the end users of the shared collection
directories.


Delegated Roles Tasks
"""""""""""""""""""""

#. A NESE coordinator at a school or a department of a NESE institutional member requests allocation of NESE resources and access to the NESE Globus institutional endpoint with the aim to administer creation of Globus shared collections for their respective research groups.

#. Research groups sponsored by a NESE institutional member place requests for Globus shared collections to their respective NESE coordinators who in turn create shared endpoints and delegate administrative tasks to their respective shared collection administrators.

#. Shared collection administrators create subdirectories of a shared collection, manage Globus users permission access to specific subdirectories and promote Globus users to the administrator role at the shared collection level.

#. Researchers use their Globus accounts to transfer data between their local endpoints and the directories located in the shared collection.

Delegated responsibilities
^^^^^^^^^^^^^^^^^^^^^^^^^^

NESE Coordinator
""""""""""""""""

* At university, school or department level

 * Holds a Globus service account 

 * Holds a NESE service Unix account

* Creates shared endpoints (shared collections) using the Globus service account

* Assigns administrator roles to Globus users at shared collection level

* Comprehends Globus interface and affairs

* Answers users' questions


Shared Collection Administrator
"""""""""""""""""""""""""""""""

* Needs a Globus account only
* Submits shared Globus collection request to their NESE coordinator
* When the shared endpoint shows up in their Globus interface
 * Creates subdirectories
 * Manages Globus user’s access controls at subdirectory level
 * Is able to promote Globus users to the administrator role at the shared collection level


Researchers, end users
"""""""""""""""""""""

* Need a Globus account only

* Install globus connect on their local machine

* Manage transfers through a Globus interface

 * Globus web interface

 * Globus command line interface

