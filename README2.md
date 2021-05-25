# Bulma

     public static SqlConnection Conetar()
        {
            SqlConnection cn = new SqlConnection("SERVER=LISSANDRA; DATABASE=Pruebas; integrated security=true;");
            cn.Open();
            return cn;
        }
        public static DataTable llenarGrid()
        {
            
            DataTable dt = new DataTable();
            string consulta = "SELECT * FROM ALUMNO";
            SqlCommand cmd = new SqlCommand(consulta, Conexion.Conetar());
            SqlDataAdapter da = new SqlDataAdapter(cmd);
            da.Fill(dt);
            return dt;
        }
        
            string insertar = "INSERT INTO ALUMNO (CODIGO,NOMBRES,APELLIDOS,DIRECCION) VALUES(@CODIGO,@NOMBRES,@APELLIDOS,@DIRECCION)";
            SqlCommand cmd = new SqlCommand(insertar, Conexion.Conetar());
            cmd.Parameters.AddWithValue("@CODIGO", tbCodigoAlumno.Text);
            cmd.Parameters.AddWithValue("@NOMBRES", tbNombre.Text);
            cmd.Parameters.AddWithValue("@APELLIDOS", tbApellido.Text);
            cmd.Parameters.AddWithValue("@DIRECCION", tbDireccion.Text);
            cmd.ExecuteNonQuery();
            MessageBox.Show("Se agrego registro");
            dataGridView1.DataSource = Conexion.llenarGrid();
