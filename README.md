# Piem3_2
# Create Trigger Oracle SQL Developer
# Create Table Evaluations_log
CREATE TABLE EVALUATIONS_LOG (
    log_timestamp TIMESTAMP,
    action varchar(30)
    );
# Test inserting record in the Table Evaluations_log for insert update delete
INSERT INTO EVALUATIONS_LOG (log_timestamp, action)
    VALUES (SYSTIMESTAMP, 'Insert');
# Create trigger for edit table Pacienti_OR
CREATE OR REPLACE TRIGGER TRIGGER_PACIENTI_OR
  AFTER INSERT OR UPDATE OR DELETE
  ON PACIENTI_OR
DECLARE
  log_action  EVALUATIONS_LOG.action%TYPE;
BEGIN
  IF INSERTING THEN
    log_action := 'Insert';
  ELSIF UPDATING THEN
    log_action := 'Update';
  ELSIF DELETING THEN
    log_action := 'Delete';
  ELSE
    DBMS_OUTPUT.PUT_LINE('This code is not reachable.');
  END IF;
  
  INSERT INTO EVALUATIONS_LOG (log_timestamp, action)
    VALUES (SYSTIMESTAMP, log_action);
END;
# Create Trigger PHPMyAdmin Insert
CREATE TABLE EVALUATIONS_LOG (
    log_timestamp TIMESTAMP,
    action varchar(30)
    );
    
INSERT INTO EVALUATIONS_LOG (log_timestamp, action)
    VALUES (CURRENT_TIMESTAMP, 'Insert');

BEGIN
INSERT INTO EVALUATIONS_LOG (log_timestamp, action)
    VALUES (CURRENT_TIMESTAMP, 'insert');
END;
